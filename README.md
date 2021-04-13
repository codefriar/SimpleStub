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

You have two broad options for installing this library. 

1. Copy the contents of force-app/main/default/classes/TestDouble.cls into your org
2. Install this package

## How do I use this?

The general mechanism for use looks like this:
```apex
 TestDouble stub = new TestDouble(SomeClass.class);
 TestDouble.Method methodToTrack = new TestDouble.MethodmethodName')
     .returning(someObject);

 stub.track(methodToTrack);

 ConsumingClass consumer = new ConsumingClass(
    (someClass) stub.generate()
 );
```

To break this down:
1. Create an instance of the TestDouble class, specifying what Apex type you want to stub in the constructor.
2. Create 'tracked' method(s). Tracked methods have a designated return value specified by you. 
3. Tell the Stub to track your tracked methods
4. Instantiate the class you want to test and inject your Stub object. 
5. Whenever your code calls a tracked method, the stub object returns the value you specified. 