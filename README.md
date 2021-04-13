# SimpleStub

## What is this?

SimpleStub is a stand alone Apex Library for dynamically creating objects that
conform to the System.StubProvider interface. 

## Background

Stub objects are fake objects that mimic real Apex Objects but with a set 
return value defined by you, the test developer. Stubs are only available in context of a Unit Test. 

## Stub Limitations

The official list of [Stub API limitations is here](https://developer.salesforce.com/docs/atlas.en-us.apexcode.meta/apexcode/apex_testing_stub_api.htm) However, in general, if can construct and dependency inject an object into your code, you can mock it. However, keep the following in mind.

### You cannot mock
- Static Methods
- Private Methods
- Properties (i.e. getters and setters)
- Triggers (Sad)
- Inner classes 
- System Types (no Account or Test.*)
- Batch classes
- Classes without a public constructor

## Installation

You have three broad options for installing this library. 

1. Copy the contents of force-app/main/default/classes/TestDouble.cls into your org
2. Install this package
3. 

## How do I use this?