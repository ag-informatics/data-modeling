# An Introductory Primer to Data Modeling
This document serves to present information on tools and strategies for creating data models using an object-oriented approach; this includes existing standards and semantic models that can be wholly adopted or modified to suit the functions or constraints of the system. The information contained in this primer is provided with the assumption that you understand the basics of object-oriented design and programming. 
**Also, keep in mind that this primer is non-exhaustive! Many different approaches to data modeling exist.**

> This primer will use the development flow of the Plant Data Service crop models as examples. You'll see them in quote blocks, like this!

## Part I: Defining the System and Evaluating Criteria 
Finding where to start in the creation of a data model can be a challenge. One of the first things you should do when creating your data models is answer the following questions:

1. What are the primary aims/purposes of the system I am modeling for?
2. What groups of data will be accessed together?
3. What variables require a selection from a list or group? This may include variables that refer (or link) back to another object.
4. Is there any spatial or temporal data in my system?
5. What are the fundamental, high-level relationships between different objects in my system?

> Using the PDS as an example (non-exhaustive):
> 1. What are the primary aims/purposes of the system I am modeling for?
>
>  **I want people to be able to access crop data to inform planting decisions. I also want this data to be accessible through various tools and platforms, and thus my system will have an API.**
>  
> 2. What groups of data will be accessed together?
> 
>  **I want several groups of data to be accessed together since the variables within these groups are practically, closely related with one another:  cover crop goal information (like how well a cover crop may perserve soil or fix nitrogen), general plant info (like scientific and common name, family of plants, etc.), data dictionaries, etc.**
>
> 3. What variables require a selection from a list or group? This may include variables that refer (or link) back to another object.
> 
> **Several variables require a selection from a list or group. Many of the cover crop goal variables, for instance, are based on contributor-defined ratings. Thus, the values of these variables will have to stay within the list of options provided by the data contributor.**
> 
> 4. Is there any spatial or temporal data in my system?
>
> **Yes. The values of plant data may change based on the location of the plant within the United States. I want the values provided by my API to be dependent on a given location. My data contributors are providing data that specifically corresponds with their organization and slice of the country, and some plants may thrive better in different biomes, latitudes, etc. The data provided by my API should also be dependent on time, since some plants may not be able to grow in certain seasons.**
>
> 5. What are the fundamental, high-level relationships between different objects in my system?
> 
>**A 'cover crop' is a child of 'plant'. A plant object may have different attribute groups such as 'abiotic stress', 'biotic stress', etc. which each have different variables defining attributes to the plant's ability to cope with specific threats or hardships.**

You may also want to consider the software you have at your disposal while you're making a model. For instance, if you are using a SQL database, you want to consider how to neatly fit your data model into rigid, static tables of values with different linked relationships (usually based upon setting a KEY which can be referred to throughout the database to refer to a specific entry elsewhere).

### Creating Entity Relationship Diagrams
Once we have answered the above questions, it is useful to create an Entity Relationship Diagram (ERD). Your ERD may may be complex, but it can help to graphically represent the relationships between objects and their different attributes. Start with the high-level relationships and move on from there.

[insert example here]

## Part II: Best Practices and Existing Standards

### Informing Entity Relationship Identification
One of the most prominent issues encountered in the data modeling process is the lack of specific standards for the creation of a model that falls under a large domain of knowledge or expertise. 

Ontologies are webs of semantic relationships between objects and their attributes. They can be extremely complex and large, but can be a great starting point for data model creation since they define relationships and provide accepted, standard language for different concepts.

[expand on this and include overview of the 5 major food/ag ontologies]
[include example of how ontology vocabulary and relationships informed PDS model creation]

### Handling Metadata
Metadata is "data that provides information on other data"[^1]. There's plenty of existing standards on metadata, but one worth noting is the [Dublin Core Metadata Element Set (DCMES)](https://www.dublincore.org/) which has been standardized internationally. The Dublin Core provides 15 "core" metadata elements for describing data [^2]:

1. Contributor
2. Coverage
3. Creator
4. Date
5. Description
6. Format
7. Identifier
8. Language
9. Publisher
10. Relation
11. Rights
12. Source
13. Subject
14. Title
15. Type

The DCMES states that these core elements may be repeated or omitted based on neecessity. 
You can view the second source listed in the [References](https://www.dublincore.org/specifications/dublin-core/dces/) for a link to the full DCMES guide describing the use case for each element.

Metadata should be incorporated into the responses your system will provide to clients. During the process of data modeling, you may find it necessary to specify metadata you want to include for each piece of information your system may output— thus, the DCMES is a fantastic tool for ensuring conformation to international standards on metadata naming and usage.


# References
[^1]: https://www.merriam-webster.com/dictionary/metadata
[^2]: https://www.dublincore.org/specifications/dublin-core/dces/

