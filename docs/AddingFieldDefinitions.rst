*********************************************************
Adding additional field definitions to Ignition Framework
*********************************************************

In this example we will be creating a third DateTime field.
In Sitecore:

#. Navigate to /sitecore/templates/Ignition/Fields/Content
#. Right-click the Content folder and select Insert → Template.

	#. Name the template DateTime3.
	#. For the base template, select “Templates/Ignition/ItemBase”
#. Assign your new template an icon: Business/32x32/calendar.png
#. On the template’s builder tab, create the field:

   * Content
   
      * DateTime3 (Datetime)


In the Ignition solution in Visual Studio:

#. Navigate to Ignition/Data/Ignition.Data/Fields
#. Create a new interface called IDateTime3.
#. Create using references for:

	#. System;
	#. Glass.Mapper.Sc.Configuration.Attributes;
	#. Ignition.Core.Models.BaseModels;

#. Above the interface declaration, add the “SitecoreType” attribute. Specify the “TemplateId” property to match the Item Id of the newly created DateTime3 template in Sitecore.
#. Make the interface declaration public, and add inheritance to IModelBase. 
#. Add the DateField3 property. Add a  SitecoreField attribute to this property, and specify the attribute’s FieldId property to match the Item Id of each respective template field in sitecore.

Your interface for the new field should look like the example below.

NB: The GUIDs are generated randomly, so your template ID and field ID will not match the IDs given in this example. You must manually copy your own IDs from Sitecore to the interface in Visual Studio. ::

	using System;
	using Glass.Mapper.Sc.Configuration.Attributes;
	using Ignition.Core.Models.BaseModels;
	namespace Ignition.Data.Fields
	{
	   [SitecoreType(TemplateId = "{60B802C3-699A-4B0E-8411-69DC59642F4E}")]
	   public interface IDateField3 : IModelBase
	   {
	       [SitecoreField(FieldId = "{5F499660-F29A-4372-BDA4-4A387FE13BF2}")]
	       DateTime DateField3 { get; set; }
	   }
	}
