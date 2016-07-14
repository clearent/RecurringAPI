<html>
<head>

<script type="text/javascript">
    window.addEventListener(
            "load",
            function(){
                processTextAreas();
            },
            false
    );
    function processTextAreas(){
        var div, ta = document.getElementsByTagName('textarea');
        // need to walk backwards because we are deleting nodes when done with them
        // and walking forward would screw up element indices
        for (var i = ta.length -1; i>=0;i--){
            console.log('--------------------------------');
            console.log(ta[i].innerHTML);
            div = document.createElement('div');
            ta[i].parentNode.insertBefore(div,ta[i]);
            div.innerHTML = '<pre>' + ta[i].innerHTML + '</pre>';
            ta[i].parentNode.removeChild(ta[i]);
        }
    }
</script>
</head>
<body>
<div class="container">
    <h3> Customer </h3>

    <p> All fields are in alphanumeric format. </p>

    <table class="api">
        <tr>
            <td><strong>Field Name</strong></td>
	     <td>Required</td>
            <td><strong>Notes</strong></td>
        </tr>
        <tr>
            <td><strong>email</strong></td>
            <td>Optional</td>
            <td>Email address for the customer </td>
        </tr>
        <tr>
            <td><strong>phone</strong></td>
		<td>Optional</td>
            <td>Contact number for the customer</td>
        </tr>
        <tr>
            <td><strong>comments</strong></td>
             <td>Optional</td>
            <td>Comments on the customer.  Note: Once updated, these comments will override previous comments. </td>
        </tr>
        <tr>
            <td><strong>customer-key</strong></td>
              <td>Response Field Only</td>
            <td>Unique key for the customer that has been created</td>
        </tr>
        <tr>
            <td><strong>first-name</strong></td>
            <td>Required</td>
            <td>First name of the customer</td>
        </tr>
        <tr>
            <td><strong>last-name</strong></td>
            <td>Required</td>
            <td>Last name of the customer</td>
        </tr>
	 <tr>
            <td><strong>billing-address</strong></td>
            <td>Optional</td>
            <td>Billing address of the customer</td>
        </tr>
	 <tr>
            <td><strong>shipping-address</strong></td>
            <td>Optional</td>
            <td>Shipping address of the customer</td>
        </tr>
        
    </table>


    <h3> Create a Customer </h3>

    <p>Customer must be created in order to set up a plan.  You can POST application/xml or application/json to the service.  Make sure you include a valid api-key in the header.</p>

    <table class="api" class="api">
        <tr>
            <td>XML Request</td>
            <td>XML Response</td>
        <tr>
            <td>
    <textarea>
   	<customer>
 		<email>testcustomer@clearent.com</email>
		 <phone>0123456789</phone>
		 <comments>Super loyal customer</comments>
 
		 <first-name>William</first-name>
		 <last-name>Biller</last-name>
 		<billing-address>
 			  <first-name>William</first-name>
 			  <last-name>Biller</last-name>
 			  <company>We Bill LLC</company>
 			  <street>123 Bill St.</street>
 			 <street2>Suite 888</street2>
  			 <city>Richmond</city>
  			 <state>MO</state>
  			 <zip>63103</zip>
   			<country>United States</country>
   			<phone>0123456789</phone>
 		</billing-address>
		 <shipping-address>
 			  <first-name>Chip</first-name>
  			 <last-name>Shipper</last-name>
  			 <company>We Ship LLC</company>
   			<street>123 Ship St.</street>
   			<street2>Suite 555</street2>
   			<city>Seattle</city>
   			<state>WA</state>
   			<zip>23227</zip>
   			<country>United States</country>
   			<phone>9876543210</phone>
		 </shipping-address>
	</customer>
    </textarea>
            </td>
            <td>
    <textarea>
   	<response>
		<code>201</code>
		<exchange-id>2eb59c9f-7128-484a-969c-ba97fe20f312</exchange-id>
		 <links>
			<rel>self</rel>
			<href>https://gateway-sb.clearent.net/rest/v2/customers/cust_dr3fiy91uyip</href>
		 </links>
		<payload type="customer">
		 <customer>
			<customer-key>cust_dr3fiY91UYIP</customer-key>
			<first-name>William2</first-name>
			<last-name>Biller2</last-name>
			 <billing-address>
				<first-name>William2</first-name>
				<last-name>Biller2</last-name>
				<company>We Bill LLC2</company>
				<street>123 Bill St.2</street>
				<street2>Suite 8882</street2>
				<city>Richmond2</city>
				<state>MO2</state>
				<zip>631032</zip>
				<country>United States2</country>
				<phone>01234567892</phone>
			 </billing-address>
			 <shipping-address>
				<first-name>Chip2</first-name>
				<last-name>Shipper2</last-name>
				<company>We Ship LLC2</company>
				<street>123 Ship St.2</street>
				<street2>Suite 5552</street2>
				<city>Seattle2</city>
				<state>WA2</state>
				<zip>232272</zip>
				<country>United States2</country>
				<phone>98765432102</phone>
			 </shipping-address>
			<email>testcustomer@clearent.com2</email>
			<phone>01234567892</phone>
			<comments>Super loyal customer2</comments>
			<links>
			 <link>
				<rel>self</rel>
				<href>https://gateway-sb.clearent.net/rest/v2/customers/cust_dr3fiY91UYIP</href>
			 </link>
			</links>	
		 </customer>
		</payload>
	 </response>

    </textarea>
            </td>
        </tr>
        <tr>
            <td>JSON Request</td>
            <td>JSON Response</td>
        <tr>
            <td>
    <textarea>
    {
           "email": "testcustomer@clearent.com",
      	   "phone": "0123456789",
           "comments": "Super loyal customer",
           "first-name":"William",
           "last-name":"Biller",
            "billing-address": {
  			"first-name":"William",			
			"last-name":"Biller",
			"company":"We Bill LLC",
			"street":"123 Bill St",
                        "street2":"Suite 888",
			"city":"Richmond",
			"state":"MO",
			"zip":"63103",
			"country":"United States",
			"phone":"0123456789"
		},
		 
            "shipping-address": {
  			"first-name":"Chip",			
			"last-name":"Shipper",
			"company":"We Ship LLC",
			"street":"123 Ship St",
                        "street2":"Suite 555",
			"city":"Seattle",
			"state":"WA",
			"zip":"23227",
			"country":"United States",
			"phone":"0123456789"
		}
 
    }
    </textarea>
            </td>
            <td>
    <textarea>
	{
  "code": "201",
  "exchange-id": "ID-clasbgw01-rps01-5f79acc9-a1c1-4438-af8f-27ca8d315c29",
  "links": [
    {
      "rel": "self",
      "href": "https://gateway-sb.clearent.net/rest/v2/customers"
    }
  ],
  "payload": {
    "payloadType": "customer",
    "customer": {
      "email": "testcustomer@clearent.com",
      "phone": "0123456789",
      "comments": "Super loyal customer",
      "customer-key": "cust_99fe153c-410f-44e8-aef7-9f5dfbf33d16",
      "first-name": "William",
      "last-name": "Biller",
      "billing-address": {
        "company": "We Bill LLC",
        "street": "123 Bill St",
        "street2": "Suite 888",
        "city": "Richmond",
        "state": "MO",
        "zip": "63103",
        "country": "United States",
        "phone": "0123456789",
        "first-name": "William",
        "last-name": "Biller"
      },
      "shipping-address": {
        "company": "We Ship LLC",
        "street": "123 Ship St",
        "street2": "Suite 555",
        "city": "Seattle",
        "state": "WA",
        "zip": "23227",
        "country": "United States",
        "phone": "0123456789",
        "first-name": "Chip",
        "last-name": "Shipper"
      },
      "links": {
        "link": [
          {
            "rel": "self",
            "href": "https://gateway-sb.clearent.net/rest/v2/customers/cust_99fe153c-410f-44e8-aef7-9f5dfbf33d16"
          },
          {
            "rel": "payment-plans",
            "href": "https://gateway-sb.clearent.net/rest/v2/payment-plans?customer-key=cust_99fe153c-410f-44e8-aef7-9f5dfbf33d16"
          }
        ]
      }
    }
  }
}
    </textarea>
            </td>
        </tr>
    </table>


    <h3>Update a Customer</h3>

    <p> You can do an HTTP PUT on any field in the customer object, and it will update that row in the object.  Keep in mind that updates to customers are first in and first out.  First, you will need to add the customer-key that was returned on the creation of the customer to the end of the URL: <BR>
     https://gateway-sb.clearent.net/rest/v2/customers/<strong>CUSTOMER-KEY-HERE</strong></p>

    <table class="api">
        <tr>
            <td>XML Request</td>
            <td>XML Response</td>
        <tr>
            <td>
    <textarea>
    	<customer>
	       <first-name>William22</first-name>
	 </customer>
    </textarea>
            </td>
            <td>
    <textarea>

    <response>
		<code>200</code>
		<exchange-id>2eb59c9f-7128-484a-969c-ba97fe20f312</exchange-id>
		 <links>
			<rel>self</rel>
			<href>https://gateway-sb.clearent.net/rest/v2/customers/cust_dr3fiy91uyip</href>
		 </links>
		<payload type="customer">
		 <customer>
			<customer-key>cust_dr3fiY91UYIP</customer-key>
			<first-name>William22</first-name>
			<last-name>Biller2</last-name>
			 <billing-address>
				<first-name>William2</first-name>
				<last-name>Biller2</last-name>
				<company>We Bill LLC2</company>
				<street>123 Bill St.2</street>
				<street2>Suite 8882</street2>
				<city>Richmond2</city>
				<state>MO2</state>
				<zip>631032</zip>
				<country>United States2</country>
				<phone>01234567892</phone>
			 </billing-address>
			 <shipping-address>
				<first-name>Chip2</first-name>
				<last-name>Shipper2</last-name>
				<company>We Ship LLC2</company>
				<street>123 Ship St.2</street>
				<street2>Suite 5552</street2>
				<city>Seattle2</city>
				<state>WA2</state>
				<zip>232272</zip>
				<country>United States2</country>
				<phone>98765432102</phone>
			 </shipping-address>
			<email>testcustomer@clearent.com2</email>
			<phone>01234567892</phone>
			<comments>Super loyal customer2</comments>
			<links>
			 <link>
				<rel>self</rel>
				<href>https://gateway-sb.clearent.net/rest/v2/customers/cust_dr3fiY91UYIP</href>
			 </link>
			</links>	
		 </customer>
		</payload>
	 </response>

    </textarea>
            </td>

        <tr>
            <td>JSON Request</td>
            <td>JSON Response</td>
        <tr>
            <td>
    <textarea>
     {
           
           "first-name":"William22"
           
    }
    </textarea>
            </td>
            <td>
    <textarea>

   {
  "code": "202",
  "exchange-id": "ID-clasbgw01-rps01-fe826724-771d-4a22-b653-31f595570a97",
  "links": [
    {
      "rel": "self",
      "href": "https:\/\/gateway-sb.clearent.net\/rest\/v2\/customers\/cust_c59ae124-d56e-4a01-87ae-bf65e6d41c39"
    }
  ],
  "payload": {
    "customer": {
      "email": "testcustomer@clearent.com",
      "phone": "0123456789",
      "comments": "Super loyal customer",
      "customer-key": "cust_c59ae124-d56e-4a01-87ae-bf65e6d41c39",
      "first-name": "William22",
      "last-name": "Biller",
      "billing-address": {
        "company": "We Bill LLC",
        "street": "123 Bill St",
        "street2": "Suite 888",
        "city": "Richmond",
        "state": "MO",
        "zip": "63103",
        "country": "United States",
        "phone": "0123456789",
        "first-name": "William",
        "last-name": "Biller"
      },
      "shipping-address": {
        "company": "We Ship LLC",
        "street": "123 Ship St",
        "street2": "Suite 555",
        "city": "Seattle",
        "state": "WA",
        "zip": "23227",
        "country": "United States",
        "phone": "0123456789",
        "first-name": "Chip",
        "last-name": "Shipper"
      },
      "links": {
        "link": [
          {
            "rel": "self",
            "href": "https:\/\/gateway-sb.clearent.net\/rest\/v2\/customers\/cust_c59ae124-d56e-4a01-87ae-bf65e6d41c39"
          },
          {
            "rel": "payment-plans",
            "href": "https:\/\/gateway-sb.clearent.net\/rest\/v2\/payment-plans?customer-key=cust_c59ae124-d56e-4a01-87ae-bf65e6d41c39"
          }
        ]
      }
    },
    "payloadType": "customer"
  }
}
    </textarea>
            </td>
        </tr>
    </table>


    <h3>Delete</h3>

    <p>You can only Delete customers that do not have plans or payments associated to them. If your customer has payments and plans, you will receive an error. You can update the status of the customer to inactive if they have plans or payments and they will be archived after 24 months. For customers that do NOT have plans or payments you can use the delete method with the URL and customer-key: https://gateway-sb.clearent.net/rest/v2/customers/<strong>CUSTOMER-KEY-HERE</strong>. You will get a 200 ok, with the object that was deleted returned to you.

    </p>

    <table class="api">
        <tr>
            <td>XML Request</td>
            <td>XML Response</td>
        <tr>
            <td>
    <textarea>
       
           Execute the delete function on the URL with the customer-key.
            In the header you will need to set the api-key and the content-type to application/xml.

    </textarea>
            </td>
            <td>
    <textarea>
         <response>
		<code>200</code>
		<exchange-id>2eb59c9f-7128-484a-969c-ba97fe20f312</exchange-id>
		 <links>
			<rel>self</rel>
			<href>https://gateway-sb.clearent.net/rest/v2/customers/cust_dr3fiy91uyip</href>
		 </links>
		<payload type="customer">
		 <customer>
			<customer-key>cust_dr3fiY91UYIP</customer-key>
			<first-name>William22</first-name>
			<last-name>Biller2</last-name>
			 <billing-address>
				<first-name>William2</first-name>
				<last-name>Biller2</last-name>
				<company>We Bill LLC2</company>
				<street>123 Bill St.2</street>
				<street2>Suite 8882</street2>
				<city>Richmond2</city>
				<state>MO2</state>
				<zip>631032</zip>
				<country>United States2</country>
				<phone>01234567892</phone>
			 </billing-address>
			 <shipping-address>
				<first-name>Chip2</first-name>
				<last-name>Shipper2</last-name>
				<company>We Ship LLC2</company>
				<street>123 Ship St.2</street>
				<street2>Suite 5552</street2>
				<city>Seattle2</city>
				<state>WA2</state>
				<zip>232272</zip>
				<country>United States2</country>
				<phone>98765432102</phone>
			 </shipping-address>
			<email>testcustomer@clearent.com2</email>
			<phone>01234567892</phone>
			<comments>Super loyal customer2</comments>
			<links>
			 <link>
				<rel>self</rel>
				<href>https://gateway-sb.clearent.net/rest/v2/customers/cust_dr3fiY91UYIP</href>
			 </link>
			</links>	
		 </customer>
		</payload>
	 </response>


    </textarea>
            </td>

        <tr>
            <td>JSON Request</td>
            <td>JSON Response</td>
        <tr>
            <td>
    <textarea>
    		Execute the delete function on the URL with the customer-key.
            In the header you will need to set the api-key and the content-type to application/xml.
    </textarea>
            </td>
            <td>
    <textarea>

    {
  "code": "200",
  "exchange-id": "ID-clasbgw01-rps01-2e0ac0dd-8a16-4ef8-8427-c67e505e447e",
  "payload": {
    "customer": {
      "email": "testcustomer@clearent.com",
      "phone": "0123456789",
      "comments": "Super loyal customer",
      "customer-key": "cust_c59ae124-d56e-4a01-87ae-bf65e6d41c39",
      "first-name": "William22",
      "last-name": "Biller",
      "billing-address": {
        "company": "We Bill LLC",
        "street": "123 Bill St",
        "street2": "Suite 888",
        "city": "Richmond",
        "state": "MO",
        "zip": "63103",
        "country": "United States",
        "phone": "0123456789",
        "first-name": "William",
        "last-name": "Biller"
      },
      "shipping-address": {
        "company": "We Ship LLC",
        "street": "123 Ship St",
        "street2": "Suite 555",
        "city": "Seattle",
        "state": "WA",
        "zip": "23227",
        "country": "United States",
        "phone": "0123456789",
        "first-name": "Chip",
        "last-name": "Shipper"
      },
      "links": {}
    },
    "payloadType": "customer"
  }
}
    </textarea>
            </td>
    </table>


   
</div>

<div class="container">
    <h3>Create a Token and associate with a customer</h3>

    <p> All fields are in alpha-numeric format</p>

    <table class="api">
        <tr>
            <td><strong>Field Name</strong></td>
	     <td>Required</td>
            <td><strong>Notes</strong></td>
        </tr>
        <tr>
            <td><strong>card</strong></td>
            <td>Required</td>
            <td>Card number to create the card token with</td>
        </tr>
        <tr>
            <td><strong>card-type</strong></td>
		<td>Required</td>
            <td>Type of card</td>
        </tr>
        <tr>
            <td><strong>exp-date</strong></td>
             <td>Required</td>
            <td>expiration date of the card </td>
        </tr>
        <tr>
            <td><strong>customer-key</strong></td>
              <td>Optional</td>
            <td>customer to associate to the token.  This is required if you want to use this token with plans/customers</td>
        </tr>
        <tr>
            <td><strong>csc</strong></td>
            <td>Required</td>
            <td>CSC of the card</td>
        </tr>
        <tr>
            <td><strong>description</strong></td>
            <td>Required</td>
            <td>description of the card (i.e. - business card) </td>
        </tr>
	 <tr>
            <td><strong>avs-address</strong></td>
            <td>Optional</td>
            <td>Optional depending on your AVS settings.  </td>
        </tr>
	 <tr>
            <td><strong>avs-required</strong></td>
            <td>Optional</td>
            <td>defaults to true. If set to false, it will not validate avs address</td>
        </tr>
         <tr>
            <td><strong>avs-zip</strong></td>
            <td>optional</td>
            <td>billing zip code of the card number</td>
        </tr>
      
    </table>


    <h3> Create a token </h3>

    <p>Plan must have a customer-key from a previously related customer.  Use url https://gateway-sb.clearent.net/rest/v2/tokens You can POST application/xml or application/json to the service.  Make sure you include a valid api-key in the header.</p>

    <table class="api" class="api">
        <tr>
            <td>XML Request</td>
            <td>XML Response</td>
        <tr>
            <td>
    <textarea>
   	<token>
    	  <card>4111111111111111</card>
  	  <card-type>VISA</card-type>
   	 <exp-date>0819</exp-date>
    	<csc>999</csc>
    	<description>test</description>
    	<avs-address>123 test</avs-address>
    	<avs-zip>123456</avs-zip>
	<customer-key>cust_dr3fiY91UYIP</customer-key>	
      </token>
    </textarea>
            </td>
            <td>
    <textarea>
   	

<response>
   <code>200</code>
   <status>success</status>
   <exchange-id>ID-STLLAP028-52999-1418744488048-0-7</exchange-id>
   <payload type="token">
      <token>
         <token-id>1100000013372201111</token-id>
         <times-used>0</times-used>
         <status>Active</status>
         <customer-key>cust_dr3fiY91UYIP</customer-key>
         <created>2014-12-16T15:50:56.549Z</created>
         <last-four-digits>1111</last-four-digits>
         <card-type>VISA</card-type>
         <description>test</description>
         <avs-address>123 test</avs-address>
         <avs-zip>123456</avs-zip>
      </token>
   </payload>
</response>

    </textarea>
            </td>
        </tr>
        <tr>
            <td>JSON Request</td>
            <td>JSON Response</td>
        <tr>
            <td>
    <textarea>

{    
    "card":"4111111111111111",
    "card-type":"VISA",
    "exp-date":"0819",
    "csc":"999",
    "avs-address":"123 test",
    "avs-zip":"123456",
    "description":"test",
    "customer-key":"cust_dr3fiY91UYIP"
}
 
    </textarea>
            </td>
            <td>
    <textarea>

{
  "code": "200",
  "status": "success",
  "exchange-id": "ID-STLLAP028-52999-1418744488048-0-10",
  "payload": {
    "token": {
      "status": "Active",
      "created": "2014-12-16T15:52:43.731Z",
      "token-id": "1100000000214291111",
      "times-used": "0",
      "last-four-digits": "1111",
      "card-type": "VISA",
      "description": "test",
	"customer-key":"cust_dr3fiY91UYIP",
      "avs-address": "123 test",
      "avs-zip": "123456"
    },
    "payloadType": "token"
  }
}
    </textarea>
            </td>
        </tr>
    </table>


    <h3>Update a Token</h3>

    <p> You can do an HTTP PUT on the field you want to modify.  There are only 3 modifiable fields on a token; customer-key, status (ACTIVE, INACTIVE, DELETED), description. Anything else you want to modify with a token, you will need to delete and re-add. First, you will need to add the token-id, that was returned on the creation of the token, to the end of the URL: 

<BR>
     https://gateway-sb.clearent.net/rest/v2/tokens/<strong>1100000000214291111</strong></p>

    <table class="api">
        <tr>
            <td>XML Request</td>
            <td>XML Response</td>
        <tr>
            <td>
    <textarea>
       <token>
    	 <description>new token</description>
    	 <customer-key>cust_dr3fiY91UYIP</customer-key>	
      </token>
    </textarea>
            </td>
            <td>
    <textarea>

   <response>
    <code>200</code>
    <status>success</status>
    <exchange-id>ID-STLLAP028-53724-1418747996621-0-10</exchange-id>
    <payload type="token">
        <token>
            <customer-key>cust_dr3fiY91UYIP</customer-key>
            <description>new token</description>
        </token>
    </payload>
</response>

    </textarea>
            </td>

        <tr>
            <td>JSON Request</td>
            <td>JSON Response</td>
        <tr>
            <td>
    <textarea>
     {    
   
   	 "description":"new token ",
	 "customer-key":"cust_dr3fiY91UYIP"
	}
    </textarea>
            </td>
            <td>
    <textarea>
{
  "code": "200",
  "status": "success",
  "exchange-id": "ID-STLLAP028-53724-1418747996621-0-16",
  "payload": {
    "token": {
      "description":"new token ",
      "customer-key":"cust_dr3fiY91UYIP"
    },
    "payloadType": "token"
  }
}
    </textarea>
            </td>
        </tr>
    </table>


    <h3>Delete</h3>

    <p>To delete a token, you can use the delete method with URL.  https://gateway-sb.clearent.net/rest/v2/tokens/<strong>1100000000214291111</strong> You will get a 200 ok, with the object that was deleted returned to you. 

    </p>

    <table class="api">
        <tr>
            <td>XML Request</td>
            <td>XML Response</td>
        <tr>
            <td>
    <textarea>
       
          Method: DELETE

	URL: https://gateway-sb.clearent.net/rest/v2/tokens/1100000013339891111

	REQUEST

	DELETE /rest/v2/tokens/1100000013339891111
	Host: gateway-sb.clearent.net
	accept: application/xml
	api-key: YOURAPIKEYHERE
	content-type: application/xml

    </textarea>
            </td>
            <td>
    <textarea>
      <response>
   <code>200</code>
    <status>success</status>
    <exchange-id>ID-STLLAP028-53724-1418747996621-0-10</exchange-id>
    <payload type="token">
        <token>
            <token-id>1100000013339891111</token-id>
            <description>Token deleted</description>
        </token>
    </payload>
</response>

    </textarea>
            </td>

        <tr>
            <td>JSON Request</td>
            <td>JSON Response</td>
        <tr>
            <td>
    <textarea>
    		 Method: DELETE

	URL: https://gateway-sb.clearent.net/rest/v2/tokens/1100000013339891111

	REQUEST

	DELETE /rest/v2/tokens/1100000013339891111
	Host: gateway-sb.clearent.net
	accept: application/json
	api-key: YOURAPIKEYHERE
	content-type: application/json
    </textarea>
            </td>
            <td>
    <textarea>

  {
  "code": "200",
  "status": "success",
  "exchange-id": "ID-STLLAP028-53724-1418747996621-0-16",
  "payload": {
    "token": {
      "token-id": "1100000001871051111",
      "description": "Token deleted"
    },
    "payloadType": "token"
  }
}
    </textarea>
            </td>
    </table>


   
</div>





<div class="container">
    <h3> Payment Plan</h3>

    <p> All fields are in alpha-numeric format.</p>

    <table class="api">
        <tr>
            <td><strong>Field Name</strong></td>
	     <td>Required</td>
            <td><strong>Notes</strong></td>
        </tr>
        <tr>
            <td><strong>plan-key</strong></td>
            <td>Response Only</td>
            <td>Unique Identifier for the plan </td>
        </tr>
        <tr>
            <td><strong>plan-name</strong></td>
		<td>Required</td>
            <td>Name of the plan</td>
        </tr>
        <tr>
            <td><strong>type</strong></td>
             <td>Required</td>
            <td>Currently can only be SUBSCRIPTION </td>
        </tr>
        <tr>
            <td><strong>customer-key</strong></td>
              <td>Required</td>
            <td>Unique key for the customer that will be associated to the plan</td>
        </tr>
        <tr>
            <td><strong>token-id</strong></td>
            <td>Required</td>
            <td>Card token that will be used to make payments on the plan</td>
        </tr>
        <tr>
            <td><strong>frequency</strong></td>
            <td>Required</td>
            <td>Frequency to make the payment. Only option is MONTHLY</td>
        </tr>
	<tr>
            <td><strong>frequency-day</strong></td>
            <td>Required</td>
            <td>Day of month to execute the payment</td>
        </tr>
	<tr>
            <td><strong>payment-amount</strong></td>
            <td>Required</td>
            <td>Amount to pay with the frequency specified </td>
        </tr>
        <tr>
            <td><strong>start-date</strong></td>
            <td>Required</td>
            <td>Day to start payment.</td>
        </tr>
       <tr>
            <td><strong>end-date</strong></td>
            <td>Required</td>
            <td>Day to end payment. Cannot be longer than 12 months</td>
        </tr>
	 <tr>
            <td><strong>status</strong></td>
            <td>Required</td>
            <td>Status of the payment plan.  ACTIVE - payments will fire.  SUSPENDED - no payments will fire, CANCELLED - no payments will fire and cannot be restarted </td>
        </tr>
        
    </table>


    <h3> Create a Plan </h3>

    <p>Plan must have a customer-key from a previously related customer.   You can POST application/xml or application/json to the service.  Make sure you include a valid api-key in the header.</p>

    <table class="api" class="api">
        <tr>
            <td>XML Request</td>
            <td>XML Response</td>
        <tr>
            <td>
    <textarea>
   	<payment-plan>
		<plan-name>Platinum Gym Membership</plan-name>
		<type>SUBSCRIPTION</type>p
		<customer-key>cust_ImZrZLriYdvj</customer-key>
		<token-id>1100008885022011111</token-id>
		<frequency>MONTHLY</frequency>
		<frequency-day>15</frequency-day>
		<frequency-month>10</frequency-month>
		<start-date>2016-08-01</start-date>
		<end-date>2016-12-01</end-date>
		<status>ACTIVE</status>
		  <payment-amount>50.00</payment-amount>
	</payment-plan>
    </textarea>
            </td>
            <td>
    <textarea>
   	<response>
		<code>201</code>
		<status>SUCCESS</status>
		<exchange-id>430b9ace-7bde-4a15-b367-6b803277b689</exchange-id>
		 <links>
		<rel>self</rel>
		<href>https://gateway-sb.clearent.net/rest/v2/payment-plans/plan_n30dbi2SFiGS</href>
		 </links>
		<payload type="payment-plan">
			 <payment-plan>
				<plan-key>plan_n30dbi2SFiGS</plan-key>
				<plan-name>Platinum Gym Membership</plan-name>
				<type>SUBSCRIPTION</type>
				<customer-key>cust_ImZrZLriYdvj</customer-key>
				<token-id>1100008885022011111</token-id>
				<frequency>MONTHLY</frequency>
				<frequency-day>15</frequency-day>
				<frequency-month>10</frequency-month>
				<payment-amount>50.00</payment-amount>
				<start-date>2016-08-01</start-date>
				<end-date>2016-12-01</end-date>
				<status>ACTIVE</status>
				<status-date>2016-01-26 19:43:04</status-date>
			 <links>
			 <link>
				<rel>self</rel>
				<href>https://gateway-sb.clearent.net/rest/v2/payment-plans/plan_n30dbi2SFiGS</href>
			 </link>
			 <link>
				<rel>customers</rel>
				<href>https://gateway-sb.clearent.net/rest/v2/customers/cust_ImZrZLriYdvj</href>
			 </link>
			 <link>
				<rel>tokens</rel>
				<href>https://gateway-sb.clearent.net/rest/v2/tokens/1100008885022011111</href>
				 </link>
			 </links>
		<metadata />
	 </payment-plan>
	</payload>
 </response>

    </textarea>
            </td>
        </tr>
        <tr>
            <td>JSON Request</td>
            <td>JSON Response</td>
        <tr>
            <td>
    <textarea>
     {
	"code": "201",
	"status": "SUCCESS",
	"exchange-id": "f1abade3-335f-41bd-b8d5-f1e55ab5550e",
	"links": [{
		"rel": "self",
		"href": "https://gateway-sb.clearent.net/rest/v2/payment-plans/plan_tz1CRPmjbuXB"
	}],
	"payload": {
		"payloadType": "payment-plan",
		"payment-plan": {
			"type": "SUBSCRIPTION",
			"frequency": "MONTHLY",
			"plan-key": "plan_tz1CRPmjbuXB",
			"plan-name": "Platinum Gym Membership",
			"customer-key": "cust_ImZrZLriYdvj",
			"token-id": "1100008885022011111",
			"frequency-day": "15",
			"frequency-month": "10",
			"payment-amount": "50.00",
			"start-date": "2016-08-01",
			"end-date": "2016-12-01",
			"status": "ACTIVE",
			"status-date": "2016-01-26 19:49:12",
			"links": {
				"link": [{
					"rel": "self",
					"href": "https://gateway-sb.clearent.net/rest/v2/payment-plans/plan_tz1CRPmjbuXB"
				}, {
					"rel": "customers",
					"href": "https://gateway-sb.clearent.net/rest/v2/customers/cust_ImZrZLriYdvj"
				}, {
					"rel": "tokens",
					"href": "https://gateway-sb.clearent.net/rest/v2/tokens/1100008885022011111"
				}]
			}
		}
	}
}
    </textarea>
            </td>
            <td>
    <textarea>
	
{
	"code": "201",
	"status": "SUCCESS",
	"exchange-id": "f1abade3-335f-41bd-b8d5-f1e55ab5550e",
	"links": [{
		"rel": "self",
		"href": "https://gateway-sb.clearent.net/rest/v2/payment-plans/plan_tz1CRPmjbuXB"
	}],
	"payload": {
		"payloadType": "payment-plan",
		"payment-plan": {
			"type": "SUBSCRIPTION",
			"frequency": "MONTHLY",
			"plan-key": "plan_tz1CRPmjbuXB",
			"plan-name": "Platinum Gym Membership",
			"customer-key": "cust_ImZrZLriYdvj",
			"token-id": "1100008885022011111",
			"frequency-day": "15",
			"frequency-month": "10",
			"payment-amount": "50.00",
			"start-date": "2016-08-01",
			"end-date": "2016-12-01",
			"status": "ACTIVE",
			"status-date": "2016-01-26 19:49:12",
			"links": {
				"link": [{
					"rel": "self",
					"href": "https://gateway-sb.clearent.net/rest/v2/payment-plans/plan_tz1CRPmjbuXB"
				}, {
					"rel": "customers",
					"href": "https://gateway-sb.clearent.net/rest/v2/customers/cust_ImZrZLriYdvj"
				}, {
					"rel": "tokens",
					"href": "https://gateway-sb.clearent.net/rest/v2/tokens/1100008885022011111"
				}]
			}
		}
	}
}
    </textarea>
            </td>
        </tr>
    </table>


    <h3>Update a Payment Plan</h3>

    <p> You can do an HTTP PUT on any field in the payment plan object, and it will update that row in the object. Keep in mind that updates to payment plans are first in and first out. First, you will need to add the plan-key, that was returned on the creation of the customer, to the end of the URL: <BR>
     https://gateway-sb.clearent.net/rest/v2/payment-plans/<strong>plan_tz1CRPmjbuXB</strong></p>

    <table class="api">
        <tr>
            <td>XML Request</td>
            <td>XML Response</td>
        <tr>
            <td>
    <textarea>
    	<payment-plan>
		<plan-name>Platinum Gym Membership 3</plan-name>
        </payment-plan>
    </textarea>
            </td>
            <td>
    <textarea>

   <response>
		<code>200</code>
		<status>SUCCESS</status>
		<exchange-id>430b9ace-7bde-4a15-b367-6b803277b689</exchange-id>
		 <links>
		<rel>self</rel>
		<href>https://gateway-sb.clearent.net/rest/v2/payment-plans/plan_n30dbi2SFiGS</href>
		 </links>
		<payload type="payment-plan">
			 <payment-plan>
				<plan-key>plan_n30dbi2SFiGS</plan-key>
				<plan-name>Platinum Gym Membership 3</plan-name>
				<type>SUBSCRIPTION</type>
				<customer-key>cust_ImZrZLriYdvj</customer-key>
				<token-id>1100008885022011111</token-id>
				<frequency>MONTHLY</frequency>
				<frequency-day>15</frequency-day>
				<frequency-month>10</frequency-month>
				<payment-amount>50.00</payment-amount>
				<start-date>2016-08-01</start-date>
				<end-date>2016-12-01</end-date>
				<status>ACTIVE</status>
				<status-date>2016-01-26 19:43:04</status-date>
			 <links>
			 <link>
				<rel>self</rel>
				<href>https://gateway-sb.clearent.net/rest/v2/payment-plans/plan_n30dbi2SFiGS</href>
			 </link>
			 <link>
				<rel>customers</rel>
				<href>https://gateway-sb.clearent.net/rest/v2/customers/cust_ImZrZLriYdvj</href>
			 </link>
			 <link>
				<rel>tokens</rel>
				<href>https://gateway-sb.clearent.net/rest/v2/tokens/1100008885022011111</href>
				 </link>
			 </links>
		<metadata />
	 </payment-plan>
	</payload>

    </textarea>
            </td>

        <tr>
            <td>JSON Request</td>
            <td>JSON Response</td>
        <tr>
            <td>
    <textarea>
     {
		"plan-name":"Platinum Gym Membership 4"
	}
    </textarea>
            </td>
            <td>
    <textarea>

  {
	"code": "200",
	"status": "SUCCESS",
	"exchange-id": "f1abade3-335f-41bd-b8d5-f1e55ab5550e",
	"links": [{
		"rel": "self",
		"href": "https://gateway-sb.clearent.net/rest/v2/payment-plans/plan_tz1CRPmjbuXB"
	}],
	"payload": {
		"payloadType": "payment-plan",
		"payment-plan": {
			"type": "SUBSCRIPTION",
			"frequency": "MONTHLY",
			"plan-key": "plan_tz1CRPmjbuXB",
			"plan-name": "Platinum Gym Membership 4",
			"customer-key": "cust_ImZrZLriYdvj",
			"token-id": "1100008885022011111",
			"frequency-day": "15",
			"frequency-month": "10",
			"payment-amount": "50.00",
			"start-date": "2016-08-01",
			"end-date": "2016-12-01",
			"status": "ACTIVE",
			"status-date": "2016-01-26 19:49:12",
			"links": {
				"link": [{
					"rel": "self",
					"href": "https://gateway-sb.clearent.net/rest/v2/payment-plans/plan_tz1CRPmjbuXB"
				}, {
					"rel": "customers",
					"href": "https://gateway-sb.clearent.net/rest/v2/customers/cust_ImZrZLriYdvj"
				}, {
					"rel": "tokens",
					"href": "https://gateway-sb.clearent.net/rest/v2/tokens/1100008885022011111"
				}]
			}
		}
	}
}
    </textarea>
            </td>
        </tr>
    </table>


    <h3>Delete</h3>

    <p>You can only Delete Plans that are not active and do not have payments associated to them.  If your plan has payments, you will receive an error. You can update the status of the plan to Canceled if it has payments and the plan will be archived after 24 months. For plans that do NOT have payments you can use the delete method with the URL.  https://gateway-sb.clearent.net/rest/v2/payment-plans/<strong>plan_tz1CRPmjbuXB</strong> You will get a 200 ok, with object that was deleted returned to you. 

    </p>

    <table class="api">
        <tr>
            <td>XML Request</td>
            <td>XML Response</td>
        <tr>
            <td>
    <textarea>
       
           Execute the delete function on the URL with the customer-key
	    https://gateway-sb.clearent.net/rest/v2/payment-plans/<strong>plan_tz1CRPmjbuXB</strong>
            In the header you will need to set the api-key and the content-type to application/xml

    </textarea>
            </td>
            <td>
    <textarea>
        <response>
		<code>200</code>
		<status>SUCCESS</status>
		<exchange-id>430b9ace-7bde-4a15-b367-6b803277b689</exchange-id>
		 <links>
		<rel>self</rel>
		<href>https://gateway-sb.clearent.net/rest/v2/payment-plans/plan_n30dbi2SFiGS</href>
		 </links>
		<payload type="payment-plan">
			 <payment-plan>
				<plan-key>plan_n30dbi2SFiGS</plan-key>
				<plan-name>Platinum Gym Membership 3</plan-name>
				<type>SUBSCRIPTION</type>
				<customer-key>cust_ImZrZLriYdvj</customer-key>
				<token-id>1100008885022011111</token-id>
				<frequency>MONTHLY</frequency>
				<frequency-day>15</frequency-day>
				<frequency-month>10</frequency-month>
				<payment-amount>50.00</payment-amount>
				<start-date>2016-08-01</start-date>
				<end-date>2016-12-01</end-date>
				<status>ACTIVE</status>
				<status-date>2016-01-26 19:43:04</status-date>
			 <links>
			 <link>
				<rel>self</rel>
				<href>https://gateway-sb.clearent.net/rest/v2/payment-plans/plan_n30dbi2SFiGS</href>
			 </link>
			 <link>
				<rel>customers</rel>
				<href>https://gateway-sb.clearent.net/rest/v2/customers/cust_ImZrZLriYdvj</href>
			 </link>
			 <link>
				<rel>tokens</rel>
				<href>https://gateway-sb.clearent.net/rest/v2/tokens/1100008885022011111</href>
				 </link>
			 </links>
		<metadata />
	 </payment-plan>
	</payload>
	 </response>


    </textarea>
            </td>

        <tr>
            <td>JSON Request</td>
            <td>JSON Response</td>
        <tr>
            <td>
    <textarea>
    		Execute the delete function on the URL with the customer-key
	    https://gateway-sb.clearent.net/rest/v2/payment-plans/<strong>plan_n30dbi2SFiGS</strong>
            In the header you will need to set the api-key and the content-type to application/json
    </textarea>
            </td>
            <td>
    <textarea>

   {
	"code": "200",
	"status": "SUCCESS",
	"exchange-id": "f1abade3-335f-41bd-b8d5-f1e55ab5550e",
	"links": [{
		"rel": "self",
		"href": "https://gateway-sb.clearent.net/rest/v2/payment-plans/plan_tz1CRPmjbuXB"
	}],
	"payloadType": "payment-plan",
	"payment-plan": {
		"type": "SUBSCRIPTION",
		"frequency": "MONTHLY",
		"plan-key": "plan_tz1CRPmjbuXB",
		"plan-name": "Platinum Gym Membership 4",
		"customer-key": "cust_ImZrZLriYdvj",
		"token-id": "1100008885022011111",
		"frequency-day": "15",
		"frequency-month": "10",
		"payment-amount": "50.00",
		"start-date": "2016-08-01",
		"end-date": "2016-12-01",
		"status": "ACTIVE",
		"status-date": "2016-01-26 19:49:12",
		"links": {
			"link": [{
				"rel": "self",
				"href": "https://gateway-sb.clearent.net/rest/v2/payment-plans/plan_tz1CRPmjbuXB"
			}, {
				"rel": "customers",
				"href": "https://gateway-sb.clearent.net/rest/v2/customers/cust_ImZrZLriYdvj"
			}, {
				"rel": "tokens",
				"href": "https://gateway-sb.clearent.net/rest/v2/tokens/1100008885022011111"
			}]
		}
	}
}
    </textarea>
            </td>
    </table>


   
</div>
</body>
</html>
