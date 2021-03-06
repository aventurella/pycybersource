pycybersource
=============

A light wrapper for Cybersource SOAP Toolkit API

This software is still alpha stage.  It supports card Auth, Capture, Sales, Auth Reversal, Credit and Void.

Requirements
------------
The only dependency is suds SOAP package (Jurko's fork), which can be found here:

    https://pypi.python.org/pypi/suds-jurko/0.6
 
Install suds:

    pip install suds-jurko==0.6
 
 
Installation
------------

    pip install git+https://github.com/bartels/pycybersource.git


Usage
-----
    from pycybersource import CyberSource
    api = CyberSource(config={'merchant_id': '...', 'api_key': ''})
    api.ccSale(
          referenceCode=randrange(0, 100000),
          payment={
             'currency': 'USD',
             'total': '88.88',
          },
          card={
              'accountNumber': '4111111111111111',
              'expirationMonth': '05',
              'expirationYear': '2018',
              'cvNumber': '123',
          },
          billTo={
              'firstName': 'Bob',
              'lastName': 'Loblaw',
              'email': 'bobt@loblaw.blah',
              'country': 'US',
              'state': 'CA',
              'city': 'Los Angeles',
              'postalCode': '90036',
              'street1': '555 Test St',
          })
       
API Methods
-----------

This api wrapper currently only implements api calls for Authorization, Capture, and Sale (auth + capture).

`CyberSource.ccAuth`: api call to perform a credit card authorization  
`CyberSource.ccCapture`:  api call to perform a capture on a previous authorization  
`Cybersource.ccSale`: api call to perform an auth & capture in one go  
`CyberSource.ccAuthReversal`: api call to perform a credit card authorization reversal  
`CyberSource.ccCredit`: api call to perform a credit card refund
`CyberSource.ccVoid`: api call to perform a credit card void

View tests to see further usage

For further documentation on Cybersource SOAP api and available api methods, visit:   http://www.cybersource.com/developers/develop/integration_methods/simple_order_and_soap_toolkit_api/
