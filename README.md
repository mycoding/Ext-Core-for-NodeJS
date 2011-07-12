Author is mycoding
Account page on Sencha forum http://www.sencha.com/forum/member.php?135053-Mycoding
email:mycodingqt@gmail.com
icq:395712335
Skype:MycodingExtJS

ExtNodeJS - framework for NodeJS on base of Ext Core and several classes of ExtJS.

It is in developing. 
At the moment it is possible to do Templating of pages, sending mails and some basic tricks.
I will try to do some samples.

Samples with explanation are here (in Russian)
http://javascript.ru/blog/mycoding/Ext-Core-dlya-NodeJS

**Templating**

var Ext = require('./extnodejs.js').Ext;
Ext.init(this);

var data = {
    name: 'Jack Slocum',     
    kids: [{
        name: 'Sara Grace',
        age:3
    },{
        name: 'Zachary',
        age:2
    },{
        name: 'John James',
        age:0
    }]
};

var tpl = new Ext.XTemplate(
    '<p>Name: {name}</p>',
    '<p>Kids: ',
    '<tpl for="kids">',
        '<tpl if="age > 1">',
            '<p>{name}</p>',
            '<p>Dad: {parent.name}</p>',
        '</tpl>',
    '</tpl></p>'
);

var html = tpl.applyTemplate(data);
console.log(html);

**Sending Email**
var Ext = require('./extnodejs.js').Ext;
Ext.init(this);
new Ext.Mail({
	to: "mycoding@mail.ru",
	from: "me@example.com",	
	subject: "Knock knock...",
	body: "Who's there?",
	success:function(){
		console.log('Success');
	},
	failure:function(err){
		console.log('Error:'+err);
	}
}).send();