# RecurringAPI
Documentation for our recurring API


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

    <p> All fields are in alpha-numeric format</p>

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
            <td>Comments on the customer.  Note: on an update these comments will override previous comments. </td>
        </tr>
        <tr>
            <td><strong>customer-profile-id</strong></td>
              <td>Response Field Only</td>
            <td>Unique key for the customer that has been created</td>
        </tr>
        <tr>
            <td><strong>first-name"</strong></td>
            <td>Required</td>
            <td>First Name of the customer</td>
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

    <p>Customer must be created in order to set up a plan.  You can POST application/xml or application/json  to the service.  Make sure you include a valid api-key in the header</p>

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
			<customer-profile-id>cust_dr3fiY91UYIP</customer-profile-id>
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
  			"first-name":"Willaim",			
			"last-name":"Biller",
			"company":"We Bill LLC",
			"street":"123 Bill St",
                        "street2":"Suite 888",
			"city":"Richmond",
			"state":"MO",
			"zip":"63103",
			"country":"United States",
			"phone":"0123456789"
		}
		 
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
  	"code": "201"
	"exchange-id": "cba7d34d-9159-40a5-99ec-eddceefb8512"
	"links": [1]
		0:  {
		"rel": "self"
		"href": "https://gateway-sb.clearent.net/rest/v2/customers/cust_dr3fiy91uyip"
		}-

	"payload": {
		"payloadType": "customer"
		"customer": {
			"email": "testcustomer@clearent.com2"
			"phone": "01234567892"
			"comments": "Super loyal customer2"
			"customer-profile-id": "cust_dr3fiY91UYIP"
			"first-name": "William2"
			"last-name": "Biller2"
			"billing-address": {
				"company": "We Bill LLC2"
				"street": "123 Bill St.2"
				"street2": "Suite 8882"
				"city": "Richmond2"
				"state": "MO2"
				"zip": "631032"
				"country": "United States2"
				"phone": "01234567892"
				"first-name": "William2"
				"last-name": "Biller2"
			}-
			"shipping-address": {
				"company": "We Ship LLC2"
				"street": "123 Ship St.2"
				"street2": "Suite 5552"
				"city": "Seattle2"
				"state": "WA2"
				"zip": "232272"
				"country": "United States2"
				"phone": "98765432102"
				"first-name": "Chip2"
				"last-name": "Shipper2"
			}-
			"links": {
				"link": [1]
					0:  {
					"rel": "self"
					"href": "https://gateway-sb.clearent.net/rest/v2/customers/cust_dr3fiY91UYIP"
					}-
-
			}-
		}-
}-
}
    </textarea>
            </td>
        </tr>
    </table>


    <h3>Update a Customer</h3>

    <p> You can do an HTTP PUT on any field in the customer object.  It will update that row in the object.  Keep in mind that updates to customers are first in and first out.  First you 

will need to add the customer-profile-id, that was returned on the creation of the customer, to the end of the URL: <BR>
     https://gateway-sb.clearent.net/rest/v2/customers/<strong>cust_dr3fiY91UYIP</strong></p>

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
			<customer-profile-id>cust_dr3fiY91UYIP</customer-profile-id>
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
           
           "first-name":"William22",
           
    }
    </textarea>
            </td>
            <td>
    <textarea>

   {
  	"code": "200"
	"exchange-id": "cba7d34d-9159-40a5-99ec-eddceefb8512"
	"links": [1]
		0:  {
		"rel": "self"
		"href": "https://gateway-sb.clearent.net/rest/v2/customers/cust_dr3fiy91uyip"
		}-

	"payload": {
		"payloadType": "customer"
		"customer": {
			"email": "testcustomer@clearent.com2"
			"phone": "01234567892"
			"comments": "Super loyal customer2"
			"customer-profile-id": "cust_dr3fiY91UYIP"
			"first-name": "William22"
			"last-name": "Biller2"
			"billing-address": {
				"company": "We Bill LLC2"
				"street": "123 Bill St.2"
				"street2": "Suite 8882"
				"city": "Richmond2"
				"state": "MO2"
				"zip": "631032"
				"country": "United States2"
				"phone": "01234567892"
				"first-name": "William2"
				"last-name": "Biller2"
			}-
			"shipping-address": {
				"company": "We Ship LLC2"
				"street": "123 Ship St.2"
				"street2": "Suite 5552"
				"city": "Seattle2"
				"state": "WA2"
				"zip": "232272"
				"country": "United States2"
				"phone": "98765432102"
				"first-name": "Chip2"
				"last-name": "Shipper2"
			}-
			"links": {
				"link": [1]
					0:  {
					"rel": "self"
					"href": "https://gateway-sb.clearent.net/rest/v2/customers/cust_dr3fiY91UYIP"
					}-
-
			}-
		}-
}-
}
    </textarea>
            </td>
        </tr>
    </table>


    <h3>Delete</h3>

    <p>You can only Delete customers that do not have plans or payments assoicated to them.  If your customer has payments and plans, you will recieve and error. You can update the status 

of the customer to inactive if it has plans or payments and the customer will be archived after 24 months.   For customers that do NOT have plans or payments you can use the delete methon 

the URL.  https://gateway-sb.clearent.net/rest/v2/customers/<strong>cust_dr3fiY91UYIP</strong> You will get a 200 ok, with object that was deleted returned to you. 

    </p>

    <table class="api">
        <tr>
            <td>XML Request</td>
            <td>XML Response</td>
        <tr>
            <td>
    <textarea>
       
           Execute the delete function on the URL with the customer-profile
	    https://gateway-sb.clearent.net/rest/v2/customers/<strong>cust_dr3fiY91UYIP</strong>
            In the header you will need to set the api-key and the content-type to application/xml

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
			<customer-profile-id>cust_dr3fiY91UYIP</customer-profile-id>
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
    		Execute the delete function on the URL with the customer-profile
	    https://gateway-sb.clearent.net/rest/v2/customers/<strong>cust_dr3fiY91UYIP</strong>
            In the header you will need to set the api-key and the content-type to application/xml
    </textarea>
            </td>
            <td>
    <textarea>

    {
  	"code": "200"
	"exchange-id": "cba7d34d-9159-40a5-99ec-eddceefb8512"
	"links": [1]
		0:  {
		"rel": "self"
		"href": "https://gateway-sb.clearent.net/rest/v2/customers/cust_dr3fiy91uyip"
		}-

	"payload": {
		"payloadType": "customer"
		"customer": {
			"email": "testcustomer@clearent.com2"
			"phone": "01234567892"
			"comments": "Super loyal customer2"
			"customer-profile-id": "cust_dr3fiY91UYIP"
			"first-name": "William22"
			"last-name": "Biller2"
			"billing-address": {
				"company": "We Bill LLC2"
				"street": "123 Bill St.2"
				"street2": "Suite 8882"
				"city": "Richmond2"
				"state": "MO2"
				"zip": "631032"
				"country": "United States2"
				"phone": "01234567892"
				"first-name": "William2"
				"last-name": "Biller2"
			}-
			"shipping-address": {
				"company": "We Ship LLC2"
				"street": "123 Ship St.2"
				"street2": "Suite 5552"
				"city": "Seattle2"
				"state": "WA2"
				"zip": "232272"
				"country": "United States2"
				"phone": "98765432102"
				"first-name": "Chip2"
				"last-name": "Shipper2"
			}-
			"links": {
				"link": [1]
					0:  {
					"rel": "self"
					"href": "https://gateway-sb.clearent.net/rest/v2/customers/cust_dr3fiY91UYIP"
					}-
-
			}-
		}-
}-
}
    </textarea>
            </td>
    </table>


   
</div>
</body>
</html>
