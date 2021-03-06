---
title: "Extending SharePoint Project Items | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: f09f6664-196d-46d6-819f-3c6500f23536
caps.latest.revision: 22
author: "gewarren"
ms.author: "gewarren"
manager: ghogen
---
# Extending SharePoint Project Items
  Create a project item extension when you want to add functionality to a type of SharePoint project item that is already installed in Visual Studio. For example, you can create an extension for the built-in **Event Receiver** or **List Definition** project items in Visual Studio, or you can create an extension for a custom project item type. You can also create an extension for all types of SharePoint project items.  
  
## Tasks for Extending SharePoint Project Items  
 To extend a project item, build a Visual Studio extension assembly that implements the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interface. For more information, see [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
 When you extend a project item, you can also add the following functionality to the project item:  
  
-   Add a shortcut menu item to the project item. The menu item appears when you open the shortcut menu for the project item in **Solution Explorer**. You open the shortcut menu by right-clicking the project item or by choosing it and then choosing the Shift + F10 keys. For more information, see [How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).  
  
-   Add a custom property to the project item. The property appears in the **Properties** window when you choose the project item in **Solution Explorer**. For more information, see [How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).  
  
 For a walkthrough that demonstrates how to create, deploy, and test a project item extension, see [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).  
  
## Understanding the Relationship Between Project Item Extensions and Project Item Instances  
 When you create a project item extension, Visual Studio loads your extension when a project item of the associated type is added to a SharePoint project. For example, if you create an extension for **Event Receiver** project items, Visual Studio loads your extension when a user adds an **Event Receiver** project item to a project. Visual Studio uses the same instance of your extension for all instances of the associated project item type. In the previous example, if the user adds a second **Event Receiver** project item to the project, the same instance of your extension is used to customize the second project item.  
  
 To access a specific instance of the project item type you are extending, handle one of the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> events of the *projectItemType* parameter in your implementation of the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> method. For example, to determine when a project item of the type you are extending is added to a project, handle the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> event. For more information, see [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
## Identifiers for SharePoint Project Items  
 Each SharePoint project item has a corresponding string identifier. You must know the identifier for a project item if you want to perform the following tasks:  
  
-   Create an extension for the project item. In this case, you must pass the identifier for the project item that you want to extend to the constructor of the <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. To create an extension for all project item types, pass the **\*** string value.  
  
-   Add the project item to a project programmatically. In this case, you must pass the identifier for the project item to the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> method.  
  
 The following table lists the identifiers for the SharePoint project items that are included with Visual Studio.  
  
|Project item name|String identifier|  
|-----------------------|-----------------------|  
|Business Data Catalog Model|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|  
|Content Type|Microsoft.VisualStudio.SharePoint.ContentType|  
|Event Receiver|Microsoft.VisualStudio.SharePoint.EventHandler|  
|Empty Element|Microsoft.VisualStudio.SharePoint.GenericElement|  
|List Definition<br /><br /> List Definition From Content Type|Microsoft.VisualStudio.SharePoint.ListDefinition|  
|List Instance|Microsoft.VisualStudio.SharePoint.ListInstance|  
|Module|Microsoft.VisualStudio.SharePoint.Module|  
|Sequential Workflow<br /><br /> State Machine Workflow|Microsoft.VisualStudio.SharePoint.Workflow|  
|Site Definition|Microsoft.VisualStudio.SharePoint.SiteDefinition|  
|Visual Web Part|Microsoft.VisualStudio.SharePoint.VisualWebPart|  
|Web Part|Microsoft.VisualStudio.SharePoint.WebPart|  
|Workflow Association Form|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|  
  
## See Also  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  