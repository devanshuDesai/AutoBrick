#### Created by Devanshu Desai & Advitya Gemawat

[Link To Webpage](https://devanshudesai.github.io/AutoBrick)

## Background and Motivation

Several commercial buildings today have sought to leverage the power of cyber-physical systems for optimal energy consumption, planned facility maintenance, machine learning (ML) applications etc to augment user experience. Their data collection / ETL methodologies, however, don’t conform to a uniform schema to enable buildings to ‘interact’ with each other or streamline the process of analytics and ML at scale. In-fact, the US building industry suffers a loss of $1.5B / year simply due to the lack of interoperable warehousing between different buildings [[1]](#ref1).

‘Brick’ is a building metadata schema directly addressing these issues by defining uniform and diverse vocabulary to represent and store data related to building objects and characteristics. ‘Brick’ offers a comprehensive schema to represent arbitrary buildings metadata, build programmatic platforms for commercial buildings, improve interoperability between different buildings, and pave the way for well-defined ways of analyses related to planned maintenance, predictive analytics, etc.

Converting arbitrary schema (csv files of building object/point labels) to Brick, or ‘Brickification’, unfortunately involves manual labor and grunt work. Brickification traditionally involves custom data transformations, object-relationship definitions, and manually plugging intermediate results into various heterogeneous frameworks to finally get a Turtle file with relationships represented in an RDF model that can be utilized by Brick. This is further motivated by the COVID-19 global pandemic where the public safety regulations in indoor environments (classrooms, offices etc) still remain a massively unsolved research question and challenge at scale.

### Traditional Workflow

The traditionally Brickification workflow involves:
1. an open-source Excel-like tool called ‘OpenRefine’, where users need to perform manual data transformations,
2. a ‘Reconciliation API’, to infer the class of specific objects in terms of Brick’s vocabulary [[6]](#ref6),
3. Entity-relationship definitions in a txt file, to utilize in the turtle file,
4. a tool called ‘Brick Builder’ to automatically convert the processed data into its turtle file [[7]](#ref7).

![Traditional Framework](https://i.ibb.co/zFpTQhv/pages-1.jpg)

As symbolized in the figure, the data transformations and most of the API injections and integrations need to be manually done by the user. The BrickBuilder tool is the only component to automate the last part of this workflow. We recognize the research and practical utility of the frameworks already created for use in the old Brickification workload. We don’t seek to reinvent the wheel here but address automation, acceleration and scalability improvements on top of these existing systems.

### Our Proposed Framework - AutoBrick

We introduce ‘AutoBrick’, an end-to-end system for automating and accelerating the conversion of point labels into turtle files with Brick terminology and which can be visualized and queried [[2]](#ref2). The tool takes in a configuration file where users can declaratively specify all details about their data and workload (related to data location, point label format details, and auxiliary parsing details).

![Proposed Framework](https://i.ibb.co/NSxDcJZ/pages-2.jpg)

AutoBrick infers and automates all needed data transformations to pre-process the point labels and extract relevant details of various units/sensors and categories related to specific building objects. AutoBrick utilizes pre-written / pre-loaded standard ER/RDF specifications and existing APIs to inject and stitch them on the pre-processed data as per the original sequence of steps followed for Brickification.

### Advantages

AutoBrick boasts versatility of usage and functionality in terms of arbitrary csv files and chosen/specified point label formats. With the project, we give the power in the hands of the user for them to decide the appropriate dataset parsing/preprocessing strategies, rather than making unverified assumptions about point label structures or utilizing unproven custom static analysis or auto-generation techniques.

Initial experiments and demos have already showcased AutoBrickify reducing ~10-15 mins of manual grunt work (as showcased in the traditional workflow) to a matter of <10 seconds, achieving orders-of-magnitude speed-ups and scalability!

### Future Work
One of the biggest challenges faced in the Brickification workflow is the predictions of Brick classes by the Reconciliation API, which has only provided accurate labels 30% of the time [[5]](#ref5). Ultimately, the turtle files need to be precisely correct for effective ETL and Analytics utilization. Though we’ve also worked on expanding the API, the same may still be subject to future updates.

The second part of augmenting the tool’s robustness relates to dealing with point label values with varying formats in the same dataset, which requires domain experts to validate additional real world use cases which can be addressed and incorporated into the same.

Last but not the least, we also explored mapping physical building spaces into virtual spaces with VR environments such as ARENA. AutoBrick also gives rise to the potential of representing building sub-systems as virtual spaces to reduce the need for engineers to physically climb into a building’s HVAC system equipment and virtually observe and ‘interact’ with sensor setpoints.

### References
[1]<a name="ref1"></a> [Brick: Towards a Unified Schema For Buildings](https://brickschema.org/papers/Brick-BuildSys-2016-Balaji.pdf)

[2]<a name="ref2"></a> [AutoBrickify](https://github.com/Advitya17/AutoBrickify)

[3]<a name="ref3"></a> [Microelectronic Embedded Systems Laboratory - UCSD](mesl.ucsd.edu)

[4]<a name="ref4"></a> [ARENA](https://arena.conix.io/)

[5]<a name="ref5"></a> [Making a Brick Model with OpenRefine + Brick Builder](https://www.youtube.com/watch?v=LKcXMvrxXzE)

[6]<a name="ref6"></a> [Reconciliation API](https://github.com/BrickSchema/reconciliation-api)

[7]<a name="ref7"></a> [Brick Builder](https://github.com/gtfierro/brick-builder)
