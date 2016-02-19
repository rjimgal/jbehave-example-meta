# jbehave-example-meta

When working with Meta filtering at Example Table level, it is needed to specify the Tag at Scenario level also. Although this is quite verbose, and people usually avoid writing more than needed. More information can be found at http://jbehave.org/reference/stable/meta-filtering.html under section `Filtering on Example Scenarios`.

However when working with Gherkin grammar, there is no such key and value when it comes to Meta. Because of this, we cannot Meta filter by Examples Table.

Instead of using JBehave's Story grammar, this project uses Gherkin to demonstrate this issue.

Project has been configured with `+smoke` as Meta filters.

There is one feature file in this project:
* `scenario_with_examples_meta_only.feature` with Meta at Examples table only.

Given current way of defining Meta tags for filtering in Examples, we would need to add `@smoke` to Scenario Meta, however that would lead in all Examples executed.


## Run using JBehave 4.0.5

From a terminal, just execute:

`mvn clean test`

The output will look like:

```
-------------------------------------------------------
 T E S T S
-------------------------------------------------------
Running org.github.rjimgal.jbehave.tests.TestRunner
Feb 19, 2016 11:00:16 AM org.springframework.context.support.AbstractApplicationContext prepareRefresh
INFO: Refreshing org.springframework.context.annotation.AnnotationConfigApplicationContext@60addb54: startup date [Fri Feb 19 11:00:16 CET 2016]; root of context hierarchy
Feb 19, 2016 11:00:16 AM org.springframework.beans.factory.support.DefaultListableBeanFactory preInstantiateSingletons
INFO: Pre-instantiating singletons in org.springframework.beans.factory.support.DefaultListableBeanFactory@64729b1e: defining beans [org.springframework.context.annotation.internalConfigurationAnnotationProcessor,org.springframework.context.annotation.internalAutowiredAnnotationProcessor,org.springframework.context.annotation.internalRequiredAnnotationProcessor,org.springframework.context.annotation.internalCommonAnnotationProcessor,testConfig,org.springframework.context.annotation.ConfigurationClassPostProcessor$ImportAwareBeanPostProcessor#0,inputSteps,propertySourcesPlaceholderConfigurer]; root of factory hierarchy
Annotation interface org.jbehave.core.annotations.UsingSteps not found in class org.github.rjimgal.jbehave.tests.TestRunner
Processing system properties {}
Using controls EmbedderControls[batch=false,skip=false,generateViewAfterStories=true,ignoreFailureInStories=false,ignoreFailureInView=false,verboseFailures=false,verboseFiltering=false,storyTimeouts=300,threads=1,failOnStoryTimeout=false]

This is a simple feature


Scenario:a scenario with examples

Given some input <param>

Examples:
|Meta:|param|
|@regression|hi there!|
|@regression|hello|
|@smoke|bye bye|

Meta[properties={narrative=Narrative[inOrderTo=,asA=,iWantTo=,soThat=], description=This is a simple feature, path=features/scenario_with_examples_meta_only.feature}] excluded by filter '+smoke'
Meta[properties={givenStories=, narrative=Narrative[inOrderTo=,asA=,iWantTo=,soThat=], examplesTable=|Meta:|param|
|@regression|hi there!|
|@regression|hello|
|@smoke|bye bye|
, description=This is a simple feature, path=features/scenario_with_examples_meta_only.feature, title=a scenario with examples}] excluded by filter '+smoke'
Meta[properties={narrative=Narrative[inOrderTo=,asA=,iWantTo=,soThat=], description=This is a simple feature, path=features/scenario_with_examples_meta_only.feature}] excluded by filter '+smoke'
Meta[properties={givenStories=, narrative=Narrative[inOrderTo=,asA=,iWantTo=,soThat=], examplesTable=|Meta:|param|
|@regression|hi there!|
|@regression|hello|
|@smoke|bye bye|
, description=This is a simple feature, path=features/scenario_with_examples_meta_only.feature, title=a scenario with examples}] excluded by filter '+smoke'
1 stories excluded by filter: +smoke

Generating reports view to '/Users/rjimenez/github/jbehave-example-meta.standalone/target/jbehave' using formats '[]' and view properties '{navigator=ftl/jbehave-navigator.ftl, views=ftl/jbehave-views.ftl, reports=ftl/jbehave-reports.ftl, nonDecorated=ftl/jbehave-report-non-decorated.ftl, decorated=ftl/jbehave-report-decorated.ftl, maps=ftl/jbehave-maps.ftl}'
Reports view generated with 0 stories (of which 0 pending) containing 0 scenarios (of which 0 pending)
Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.715 sec

Results :

Tests run: 1, Failures: 0, Errors: 0, Skipped: 0
```


## Run using JBehave 4.1-SNAPSHOT with PR applied

From a terminal, just execute:

`mvn clean test -Pjbehave41`

The output will look like (`bye bye` is printed):

```
-------------------------------------------------------
 T E S T S
-------------------------------------------------------
Running org.github.rjimgal.jbehave.tests.TestRunner
Feb 19, 2016 11:01:15 AM org.springframework.context.support.AbstractApplicationContext prepareRefresh
INFO: Refreshing org.springframework.context.annotation.AnnotationConfigApplicationContext@60addb54: startup date [Fri Feb 19 11:01:15 CET 2016]; root of context hierarchy
Feb 19, 2016 11:01:15 AM org.springframework.beans.factory.support.DefaultListableBeanFactory preInstantiateSingletons
INFO: Pre-instantiating singletons in org.springframework.beans.factory.support.DefaultListableBeanFactory@64729b1e: defining beans [org.springframework.context.annotation.internalConfigurationAnnotationProcessor,org.springframework.context.annotation.internalAutowiredAnnotationProcessor,org.springframework.context.annotation.internalRequiredAnnotationProcessor,org.springframework.context.annotation.internalCommonAnnotationProcessor,testConfig,org.springframework.context.annotation.ConfigurationClassPostProcessor$ImportAwareBeanPostProcessor#0,inputSteps,propertySourcesPlaceholderConfigurer]; root of factory hierarchy
Annotation interface org.jbehave.core.annotations.UsingSteps not found in class org.github.rjimgal.jbehave.tests.TestRunner
Processing system properties {}
Using controls EmbedderControls[batch=false,skip=false,generateViewAfterStories=true,ignoreFailureInStories=false,ignoreFailureInView=false,verboseFailures=false,verboseFiltering=false,storyTimeouts=300,threads=1,failOnStoryTimeout=false]

This is a simple feature


Scenario:a scenario with examples

Given some input <param>

Examples:
|Meta:|param|
|@regression|hi there!|
|@regression|hello|
|@smoke|bye bye|

Meta[properties={narrative=Narrative[inOrderTo=,asA=,iWantTo=,soThat=], description=This is a simple feature, path=features/scenario_with_examples_meta_only.feature}] excluded by filter '+smoke'
Meta[properties={regression=}] excluded by filter '+smoke'
Meta[properties={regression=}] excluded by filter '+smoke'
Meta[properties={narrative=Narrative[inOrderTo=,asA=,iWantTo=,soThat=], description=This is a simple feature, path=features/scenario_with_examples_meta_only.feature}] excluded by filter '+smoke'
Running story features/scenario_with_examples_meta_only.feature
bye bye
Generating reports view to '/Users/rjimenez/github/jbehave-example-meta.standalone/target/jbehave' using formats '[]' and view properties '{navigator=ftl/jbehave-navigator.ftl, views=ftl/jbehave-views.ftl, reports=ftl/jbehave-reports.ftl, nonDecorated=ftl/jbehave-report-non-decorated.ftl, decorated=ftl/jbehave-report-decorated.ftl, maps=ftl/jbehave-maps.ftl}'
Reports view generated with 0 stories (of which 0 pending) containing 0 scenarios (of which 0 pending)
Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.808 sec

Results :

Tests run: 1, Failures: 0, Errors: 0, Skipped: 0
```
