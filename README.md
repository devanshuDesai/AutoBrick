## Background and Motivation

Several commercial buildings today have sought to leverage the power of cyber-physical systems for optimal energy consumption, planned facility maintenance, machine learning (ML) applications etc to augment user experience. Their data collection / ETL methodologies, however, don’t conform to a uniform schema to enable buildings to ‘interact’ with each other or streamline the process of analytics and ML at scale. In-fact, the US building industry suffers a loss of $1.5B / year simply due to the lack of interoperable warehousing between different buildings [1].

‘Brick’ is a building metadata schema directly addressing these issues by defining uniform and diverse vocabulary to represent and store data related to building objects and characteristics, and has delivered promising results in terms of uniformly representing data for diverse buildings across various locations.

Converting arbitrary schema (csv files of building object/point labels) to Brick, or ‘Brickification’, unfortunately involves manual labor and grunt work in terms of custom data transformations, object-relationship definitions, and manually plugging intermediate results into various heterogeneous frameworks to finally get a Turtle file that can be utilized by Brick. This is further motivated by the COVID-19 global pandemic where the public safety regulations in indoor environments (classrooms, offices etc) still remain a massively unsolved research question and challenge at scale.

### Traditional Workflow

The current Brickification workflow involves:
1. an open-source Excel-like tool called ‘OpenRefine’, where users need to perform manual data transformations,
2. a ‘Reconciliation API’, to infer the class of specific objects in terms of Brick’s vocabulary,
3. Entity-relationship definitions in a txt file, to utilize in the turtle file,
4. a tool called ‘Brick Builder’ to automatically convert the processed data into its turtle file.

*(Add Image Here)*

As symbolized in the figure, the data transformations and most of the API injections and integrations need to be manually done by the user. The BrickBuilder tool is the only component to automate the last part of this workflow. We recognize the research and practical utility of the frameworks already created for use in the old Brickification workload. We don’t seek to reinvent the wheel here but address automation, acceleration and scalability improvements on top of these existing systems.

### Our Proposed Framework - AutoBrick

We introduce ‘AutoBrick’, an end-to-end system for automating and accelerating the conversion of point labels into turtle files with Brick terminology and which can be visualized and queried [2]. The tool takes in a configuration file where users can declaratively specify all details about their data and workload (related to data location, point label format details, and auxiliary parsing details).

*(Add Image Here)*

AutoBrick infers and automates all needed data transformations to pre-process the point labels and extract relevant details of various units/sensors and categories related to specific building objects. AutoBrick utilizes pre-written / pre-loaded standard ER/RDF specifications and existing APIs to inject and stitch them on the pre-processed data as per the original sequence of steps followed for Brickification.

### Advantages

AutoBrick boasts versatility of usage and functionality in terms of arbitrary csv files and chosen/specified point label formats. With the project, we give the power in the hands of the user for them to decide the appropriate dataset parsing/preprocessing strategies, rather than making unverified assumptions about point label structures or utilizing unreliable custom static analysis or auto-generation techniques.

Initial experiments and demos have already showcased AutoBrickify reducing ~10-15 mins of manual grunt work (as showcased in the traditional workflow) to a matter of <10 seconds, achieving orders-of-magnitude speed-ups and scalability!

### Future Work
With AutoBrick, we plan to expand the API to add support for novel real-world use cases by consulting the research lab originally involved in Brick [3]. We also plan to leverage the output turtle files and build proof-of-concept virtual spaces for buildings using VR environments such as ARENA [4].

### References
1. (Brick: Towards a Unified Schema For Buildings)[https://brickschema.org/papers/Brick-BuildSys-2016-Balaji.pdf]
2. (AutoBrickify)[https://github.com/Advitya17/AutoBrickify]
3. (Microelectronic Embedded Systems Laboratory - UCSD)[mesl.ucsd.edu]
4. (ARENA)[https://arena.conix.io/]
