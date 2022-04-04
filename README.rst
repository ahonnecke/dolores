=======
snifter
=======


    Listen to and inspect AWS SNS topic data

=======
Help
=======

.. code-block:: python

    $ snifter --help
    usage: snifter [-h] [-p PROFILE] [-d] [-t TOPIC]

    Listen to an SNS topic

    optional arguments:
      -h, --help            show this help message and exit
      -p PROFILE, --profile PROFILE
                            AWS profile name
      -d, --debug           Drop into debugger to inspect message
      -t TOPIC, --topic TOPIC
                            SNS topic name

=======
Login
=======
![snifter_login](https://user-images.githubusercontent.com/419355/161607497-637e13e6-32a2-4d70-8336-9153691d4d61.gif)

=======
Listening
=======
![snifter_listen](https://user-images.githubusercontent.com/419355/161607493-9fd60169-0aab-4637-b709-593cf315e6eb.gif)

=======
Inspecting (with debug on)
=======
![snifter_debug](https://user-images.githubusercontent.com/419355/161607489-40bea93f-a5b3-4056-888b-944916151822.gif)

.. code-block:: python
    $ snifter -d
    Profile was not passed, choose a profile: dev-power
    Choose topic: tim-manager-events
    Listening...
    Listening...
    Listening...
    Listening...
    Listening...
    Listening...
    Listening...
    Listening...
    Dropping into debugger for inspection
    Local message variable is 'm'
    PDB commands: 'c' to continue, 'exit()' to exit
    (Pdb++)
    (Pdb++) list
    143  	                print("PDB commands: 'c' to continue, 'exit()' to exit")
    144  	                breakpoint()
    145  	            else:
    146  	                print(f"Recieved message, {m.body}")
    147
    148  ->	            m.delete()
    149
    150  	        print("Listening...")
    151  	        sleep(1)
    152
    153
    (Pdb++) print(m.body)
    {
      "Type" : "Notification",
      "MessageId" : "126fab4d-4c52-58d9-9b28-f18875ddba13",
      "TopicArn" : "arn:aws:sns:us-west-2:024726604032:tim-manager-events",
      "Message" : "{\"id\": \"68860414-976a-4c2c-bfc5-134d06a41176\", \"tenant_name\": \"DEV\", \"delivery_stop_time\": \"2022-04-04T18:29:32Z\", \"delivery_start_time\": \"2022-04-04T18:21:32Z\", \"rsus\": [\"8bfacac8-9c8f-41e6-b9a3-09641913da8a\", \"590d0953-444d-4f0a-842d-3ad425394baf\", \"444ed7e8-7ffc-4261-8649-c06e77924f16\", \"e7e259da-926c-4c0e-93cd-a8507bda76b3\", \"d4d7cc04-b98a-4ad8-b9b6-801966c84f68\"], \"status\": \"active\", \"geo_json_region\": {\"geometry\": {\"coordinates\": [[-104.78268881199995, 39.80739706900005], [-104.78147999999999, 39.807390000000055], [-104.78147999999999, 39.80642254800006]], \"type\": \"LineString\"}}, \"path_directionality\": \"FORWARD\", \"tim_duration_min\": 8, \"itis_codes\": [\"1025\", \"7196\", \"12579\", \"8720\"], \"itis_texts\": [\"WORK ZONE WARNING\", \"!35 MPH ADVISED\"], \"message_type\": \"WZW\", \"advised_mph\": 35, \"event_id\": null, \"created_by\": \"cognito:ashton.honnecke@us.panasonic.com\", \"updated_by\": null, \"successful_rsu_ids\": [\"444ed7e8-7ffc-4261-8649-c06e77924f16\"], \"failed_rsu_ids\": [\"590d0953-444d-4f0a-842d-3ad425394baf\", \"8bfacac8-9c8f-41e6-b9a3-09641913da8a\", \"d4d7cc04-b98a-4ad8-b9b6-801966c84f68\", \"e7e259da-926c-4c0e-93cd-a8507bda76b3\"], \"created_time\": \"2022-04-04T18:21:59Z\", \"hidden_time\": null, \"hidden_by\": null, \"updated_time\": null, \"width_cm\": 6000, \"curve_id\": null, \"curve_direction\": null, \"curve_angle\": null, \"notification_region\": {\"width_cm\": 6000, \"path_directionality\": \"FORWARD\", \"region\": {\"path\": [[\"-104.78268881199995\", \"39.80739706900005\"], [\"-104.78147999999999\", \"39.807390000000055\"], [\"-104.78147999999999\", \"39.80642254800006\"]]}}, \"topic_version\": 1}",
      "Timestamp" : "2022-04-04T18:22:07.397Z",
      "SignatureVersion" : "1",
      "Signature" : "Rp/kCiKaT+34vajMkBLJMAtEFo2qzxzQ1fE+8mJNuOrU7I9zbyKs+c+soYAYOcicP6MnIAjxEswKlXM4cHRB2DFf5wIGet6lwwmuicTM5pbh4OsKcjTXS6FINjCfwN+yIwu97l3hQ1KDRGrJAbSlBEbCPTrUfkWRFI0eDQzC3xz31nP5cBP3qUYDbYQbVGYXdhGyRkVYxnYM1QL82x6Q9rSlNEZbbbQ+ZrrZUTVvhYPF18BDaXC4KW4jo1x4Ujo/CxtIci9xVsIhQC84hFwSlbd/h8nhV6zoikT9W3QikGcHImNKnhdKfnTCJIFkpfJfrG2X/DsUu32Op37tc+YfUA==",
      "SigningCertURL" : "https://sns.us-west-2.amazonaws.com/SimpleNotificationService-7ff5318490ec183fbaddaa2a969abfda.pem",
      "UnsubscribeURL" : "https://sns.us-west-2.amazonaws.com/?Action=Unsubscribe&SubscriptionArn=arn:aws:sns:us-west-2:024726604032:tim-manager-events:549fa881-9414-48b3-8eb6-e58d5c81bb65",
      "MessageAttributes" : {
        "messageType" : {"Type":"String","Value":"TIMS_CREATED"}
      }
    }
    (Pdb++) --KeyboardInterrupt--
