********************************************
Accessing the component's Datasource setting
********************************************

In your agent, inheriting AbstractViewAgent provides access to the (IModelBase)Datasource property. By default, the Datasource propertry contains the current component's display name, URI, child items, and other commonly-used metadata. The full list of default Datasource properties is viewable in the code files:

https://github.com/sitecoreignition/SitecoreIgnition/blob/master/Ignition.Core/Models/BaseModels/IModelBase.cs

https://github.com/sitecoreignition/SitecoreIgnition/blob/master/Ignition.Core/Models/BaseModels/IModelBaseWithMetadata.cs

To access the datasource's Ignition fields, you must cast the datasource to the model type of your component:


::

    // ./MyComponent/Models/IMyComponent.cs:
    [SitecoreType(TemplateId = "{012345678-9ABC-DEF0-1234-56789ABCDEF0}", AutoMap = true)]
    public interface IMyComponent : IHeading, ISubtitle, IImage
    {
    }

    // ./MyComponent/Agents/MyComponentAgent.cs:
    public class MyComponentAgent : AbstractViewAgent<MyComponentViewModel>
    {
        public MyComponentAgent(IRepository repository, SitecoreData sitecoreData) : base(repository, sitecoreData)
        {
        }

        public override void PopulateModel() 
        {
            // Only properties defined in IModelBase are accessible in the Datasource variable.
            var ds = Datasource as IMyComponent;
            // All Datasource properties plus ds.Heading, ds.Subtitle, and ds.Image are now accessible.
        }
    }

