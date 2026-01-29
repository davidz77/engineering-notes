#### Intro to software engineering:
nato conference started to address issue of defining field of swe but software crisis too
software eng includes multi version/person development 
programming does not involve multiple versions of a program
good programmer != good swe

software = malleable, complex, useful
software varies:
size, human interaction, req stability, security, reliability, portability, cost

software dev process (productivity) -> software system (quality) -> software users (experience) (own focus on goals) 
users don't have to be customers
good, fast, cheap is goal

req, design
implementation, integration, maintenance
#### software process:
project management
	project initiation
	project planning
	project monitoring/control
pre-development
	concept exploration
	system allocation
	software importation
development
	software req
	design impl
post dev
	installation
	operation/support
	maintenance
	retirement
support
	eval
	software config management
	doc dev
	training
agile
	XP, scrum
plan driven/formal
	waterfall, spiral, RUP, cleanroom
distributed/open source 
	bazaar

Plan driven methodologies:
waterfall model theoretical:
	req -> design -> implementation -> integration/testing -> maintenance
	can't start next phase until finish prev phase
spiral model:
	determine objectives -> identify/resolve risks -> dev/test -> plan for next iteration
RUP:
	inception (make decision) -> elaboration (make initial version) -> construction -> transition 
	can have multiple iterations of the same phases

agile software dev:
XP (iterative):
	planning game for req
	test driven dev
	refactor for design
	pair programming for dev
	CICD

AGILE vs Plan driven:
size, criticality, dynamism, personnel, culture
size small = agile, big = driven
critical = plan driven, not critical = AGILE
shit changing? = agile, stuff staying same = plan
shit people = plan, good people = agile

customers write user stories 
developers estimate time for each story
story points - estimate using expert opinion, analogy, disaggregation, planning poker

scheduling:
list of tasks, resources per task, schedule tasks (compete for resources/depend on each other)
PERT - program evaluation and review technique
Gannt chart
	start to start = task cannot start until predecessor starts
	finish to finish = task cannot end until predecessor ends

task finished?
	must be objective
	different tasks are evaluated differently

#### req. engineering:
req are about what, about what stakeholder needs to achieve goals
functional req - functional effects
non-function req. - performance/speed/look

descriptive statements - natural law
prescriptive statements - desirable properties of system
shall = mandatory, should = desirable, will - reference to the future, not under control of system

system-as-is -> system-to-be
req elicitation:
	identify boundaries
	understand context
	identify stakeholders
	identify stakeholders' goals
	collect tasks
	identify feasibility and risk
UML - actors and use cases
#### software design + arch: 
principal design decisions about system
prescriptive - as designed
descriptive - as implemented

software architect - getting inputs, providing info, architecting

model view controller
#### oo patterns pt 1:
uml arrows:
black diamond + solid = composition (child can NOT exist independent from parent)
hollow arrow + solid = inheritance
hollow arrow + dotted = realization/implementation
hollow diamond + solid= aggregation (child can exist independent from parent)
arrow + dotted = dependency 

#### oo patterns pt 2: 8 (9 questions)
design pattern - description of communicating objects/classes that are customized to solve a general problem
creational patterns
	abstract factory, builder, factory method,
structural patterns
	composition of classes/objects
behavioral patterns
	characterize classes/object interact and distribute responsibility

observer pattern:
	no concrete - interface
	concrete - the actual code doing shit

composite pattern:

#### software test pt 1: 7 (15 questions)

#### software test pt 2: 8 (16 questions)
assume, arrange, act, assert
#### debugging: 8 (15 questions)

