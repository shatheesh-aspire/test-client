#Aria7 Java SDK

The Java SDK is a library that makes it easy to use the [Aria7](http://www.ariasystems.com/) web services of Core API / Object-Query API / AdminTools API in your java application.

## Installation

Make sure the java version is 1.7.
```
* C:\Users>java -version
* java version "1.7.0_09"
* Java(TM) SE Runtime Environment (build 1.7.0_09-b05)
* Java HotSpot(TM) Client VM (build 23.5-b02, mixed mode, sharing)
```
Download the Java SDK library Aria7SDK.jar from the dist folder and the dependent third-party libraries from the download folder of this java_sdk_A7 repository.

Import the above libraries to the java application from where the Aria APIs are to be called.

## Usage

1. The AriaBillingCompleteM class has methods for each Core API of Aria and it can be instantiated in any of the following ways mentioned below.

  ##### Core API

  ```java 
  /**
   * Creates a client to the Aria APIs.
   * Instances are threadsafe.
   *
   * Since construction is relatively costly, users should reuse a single instance across calls and across threads.   
   */
   String endpointURI = "https://secure.future.stage.ariasystems.net/api/ws/api_ws_class_dispatcher.php";
  AriaBillingCompleteM ariaBillingComplete = new com.aria.sdk.classes.AriaBillingCompleteMRest(endpointURI);
  ```

  ```java 
  /**
   * Creates a client to the Aria APIs using the provided Jersey client.
   * Instances are threadsafe.
   *
   * Since construction is relatively costly, users should reuse a single instance across calls and across threads.   
   */
  String endpointURI = "https://secure.future.stage.ariasystems.net/api/ws/api_ws_class_dispatcher.php";
  AriaBillingCompleteM ariaBillingComplete = new com.aria.sdk.classes.AriaBillingCompleteMRest(endpointURI, Client.create(new DefaultClientConfig()));
  ```
  ##### Object-Query APIs

  Similarly, to access the Object-Query APIs, instantiate the com.aria.sdk.classes.AriaBillingIntegrationM as follows
  
   ```java 
  /**
   * Creates a client to the Aria APIs.
   * Instances are threadsafe.
   *
   * Since construction is relatively costly, users should reuse a single instance across calls and across threads.   
   */
  String endpointURI = "https://secure.future.stage.ariasystems.net/api/AriaQuery/objects.php";
  AriaBillingIntegrationM ariaBillingIntegration = new com.aria.sdk.classes.AriaBillingIntegrationMRest(endpointURI);
  ```

  ```java 
  /**
   * Creates a client to the Aria APIs using the provided Jersey client.
   * Instances are threadsafe.
   *
   * Since construction is relatively costly, users should reuse a single instance across calls and across threads.   
   */
  String endpointURI = "https://secure.future.stage.ariasystems.net/api/AriaQuery/objects.php";
  AriaBillingIntegration ariaBillingIntegration = new com.aria.sdk.classes.AriaBillingIntegrationMRest(endpointURI, Client.create(new DefaultClientConfig()));
  ```
  
  ##### AdminTools APIs

  Similarly, to access the AdminTools APIs, instantiate the com.aria.sdk.classes.AriaBillingAdministrationM as follows
  
  ```java 
  /**
   * Creates a client to the Aria APIs.
   * Instances are threadsafe.
   *
   * Since construction is relatively costly, users should reuse a single instance across calls and across threads.   
   */
  String endpointURI = "https://admintools.future.stage.ariasystems.net/index.php/Dispatcher/index";
  AriaBillingAdministrationM ariaBillingAdministration = new com.aria.sdk.classes.AriaBillingAdministrationMRest(endpointURI);
  ```

  ```java 
  /**
   * Creates a client to the Aria APIs using the provided Jersey client.
   * Instances are threadsafe.
   *
   * Since construction is relatively costly, users should reuse a single instance across calls and across threads.   
   */
   String endpointURI = "https://admintools.future.stage.ariasystems.net/index.php/Dispatcher/index";
   AriaBillingAdministrationM ariaBillingAdministration = new com.aria.sdk.classes.AriaBillingAdministrationMRest(endpointURI, Client.create(new DefaultClientConfig()));
  ```
  
	* In the case of Core API, "https://secure.future.stage.ariasystems.net/api/ws/api_ws_class_dispatcher.php" is the dispatcher url.
	* In the case of Object-Query, the dispatcher url will be similar to 	"https://secure.future.stage.ariasystems.net/api/AriaQuery/objects.php".
	* In the case of AdminTools, the dispatcher url will be similar to "https://admintools.future.stage.ariasystems.net/index.php/Dispatcher/index".
  
2. Call the desired API method on the corresponding instance by passing appropriate inputs objects, client_no and auth_key. Either of the two approaches " Passing input directly as parameters" or "Using a Parameters Builder" which are listed below can be used to call the desired API.
##### Passing input directly as parameters
	In the following example, a sample client_no of 100 and auth_key as 'zzzzz' is used.
	```java 
	    // Form the api inputs
	    com.aria.common.shared.core.eom.EventListRow eventListRow1 = new com.aria.common.shared.core.eom.EventListRow();
	    eventListRow1.setEventList(120L);
	    com.aria.common.shared.core.eom.EventListRow eventListRow2 = new com.aria.common.shared.core.eom.EventListRow();
	    eventListRow2.setEventList(130L);
	    com.aria.common.shared.core.eom.EventListArray eventListArray = new com.aria.common.shared.core.eom.EventListArray();
	    eventListArray.getEventListRow().add(eventListRow1);
	    eventListArray.getEventListRow().add(eventListRow2);
	
	    // Call the API
	    Map<String,Object> hashMapReturnValues = ariaBillingComplete.subscribeEventsM(100L,"zzzz", eventListArray);
	  ```
	##### Using a Parameters Builder
		In the following example, a sample client_no of 100 and auth_key as 'zzzzz' is used.
		
	```java 
	    // Form the api inputs
	com.aria.common.shared.core.eom.EventListRow eventListRow1 = new com.aria.common.shared.core.eom.EventListRow();
	    eventListRow1.setEventList(120L);
	com.aria.common.shared.core.eom.EventListRow eventListRow2 = new com.aria.common.shared.core.eom.EventListRow();
	    eventListRow2.setEventList(130L);
	com.aria.common.shared.core.eom.EventListArray eventListArray = new com.aria.common.shared.core.eom.EventListArray();
	eventListArray.getEventListRow().add(eventListRow1);
	eventListArray.getEventListRow().add(eventListRow2);
	/**
	* Using a builder object. 
	* The createBuilder accepts (getClientNo(), getAuthKey()) or list of required parameters as argument. The parameters
	* that are to be passed to * be API can be chained in the builder object as shown below . ex : withLimit(1L).
	*/
	com.aria.common.shared.core.eom.builder.SubscribeEventsMParameters.SubscribeEventsMParametersBuilder builder = com.aria.common.shared.core.eom.builder.SubscribeEventsMParameters.createBuilder(getClientNo(), getAuthKey());
	builder.withEventListArray(eventListArray);
	/**
	* builder.build() will generate a paramter class of that API and will be passed to getPlanInstanceInformationM. Here   
	* getPlanInstanceInformationM is overloaded to accept a parameter object.
	*/
	hashMapReturnValues = getBaseAriaBilling().subscribeEventsM(builder.build());
	```
3. The API response values can be read from the Map object returned by the API method as shown below.

            // Read the output from the map as below.
            System.out.println("error_code: " + hashMapReturnValues.get("error_code"));
            System.out.println("error_msg: " + hashMapReturnValues.get("error_msg"));

##More Information

Check out [Aria Developer Central](http://developer.ariasystems.net) for more examples, details, and support on [Aria](http://www.ariasystems.com/) services and features.

