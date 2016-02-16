Conditions from Time Series 
===========================

The Falkonry Service was built in response to the need to make condition recognition 
ubiquitous and easily accessible by system operators. The service is easily added to any 
application that manages time-series data and does not require data scientists or custom 
software development.  

Problem solved by Falkonry
--------------------------

The Falkonry Service is used to transform signal data into real-time assessments of 
condition.  It is not, however, a machine learning toolkit for data scientists.  Users of 
the service simply supply it with signal data and any available examples of verified 
conditions and it will learn to recognize conditions.  Once it learns conditions it will 
recognize those conditions in new data.  As it accumulates data and additional verified 
examples, it continues to learn and improve its ability to recognize or ‘assess’ conditions.

In a nutshell, then, the `Falkonry Service <using/>`_ is a machine learning machine that combines 
condition learning and condition assessment in an easy to use package that does not require 
professional data scientist or software developers.

The Falkonry Service design was inspired by frustration with how excruciatingly hard it is
to extract basic condition understanding out of the copious amounts of time-series data 
that surround us and the difficulty in getting a team of specialists to work together to 
solve this problem.  In a typical condition assessment need situation, the following 
realities exists:

- the data consists of multiple signals with complex behavior, and no human could 
  reasonably identify meaningful patterns in the data by inspection or through construction 
  of rules or thresholds.
- there is no available team of data scientists and software developers, nor the budget 
  and patience to execute a multi-month project.
- there is no pre-existing well-formed training data set from which to build a condition model.
- not all conditions are known in advance.
- system conditions evolve over time.

By focused delivery of pre-packaged multi-signal classification, the Falkonry Service is 
able to addresses these realities for a wide range of problems.  Certainly, custom data 
science and software development projects can deliver greater accuracy or solution 
granularity but such an approach is rarely viable.  In the world of condition recognition 
problems, we need to buy the vast majority of our clothing off the rack, and only very 
rarely can we hire the fashion designer and a professional tailor.
