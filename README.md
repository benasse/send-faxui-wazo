# send-faxui-wazo
A small web interface to send faxes with Wazo, developed quick and dirty, don't be afraid to propose improvements!

---

Firstly add a wazo user named *userfax*. Set a *$ecretP@ssword* for him (don't forget to activate authentication in the user parameters)

Then go to *__Credential > identities__* then select your *userfax* user and add the following policies : wazo-auth-internal & wazo-calld-internal. (the best would be to create two policies that only allow you to retrieve a token and use the fax api)

Now you are ready to send faxes !


Final step, the gui : I used docker to set-up easily the interface :

1. Edit `html/index.php` and set your wazo server IP

2. Get the source code and build the image
` docker built -t send-faxui-wazo /path/to/source/code `

3. Run the conaitner 
` docker run -d -p 80:80 -e WAZO_FAX_USER="userfax@wazo.com" -e WAZO_FAX_PASSWD="$ecretP@ssword" -e WAZO_FAX_NAME="IT fax" -e CALLER_ID="0123456789" --name=it-fax --restart=always send-faxui-wazo `

4. Browse at hostIpAdress and enjoy the send-faxui-wazo


