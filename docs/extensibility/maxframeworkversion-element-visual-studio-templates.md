---
title: "MaxFrameworkVersion-Element (Visual Studio-Vorlagen) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<MaxFrameworkVersion>-Element (Visual Studio-Vorlagen)"
  - "MaxFrameworkVersion-Element (Visual Studio-Vorlagen)"
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# MaxFrameworkVersion-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt die höchste Version von .NET Framework an, die für die Vorlage erforderlich ist.  Sie bestimmt, ob die Vorlage im Abschnitt **Vorlagen** des Dialogfelds **Neues Projekt hinzufügen** angezeigt werden soll, basierend auf dem Wert, der im Feld **Framework\-Zielversion** des Dialogfelds **Neues Projekt hinzufügen** ausgewählt wurde.  
  
## Syntax  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
 Keine.  
  
### Untergeordnete Elemente  
 Keine.  
  
### Übergeordnete Elemente  
  
|Element|Description|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|  
  
## Textwert  
 Ein Textwert ist erforderlich.  
  
 Der Text muss die höchste Versionsnummer von .NET Framework sein, die von der Vorlage zugelassen wird.  
  
## Hinweise  
 `MaxFrameworkVersion` ist ein optionales Element.  Das Element im `TemplateData`\-Abschnitt der VSTEMPLATE\-Datei fungiert als Filter für den Abschnitt **Vorlagen** des Dialogfelds **Neues Projekt hinzufügen**.  Nur Vorlagen, deren .NET Framework\-Anforderungen kleiner sind als `MaxFrameworkVersion`\-Elementwerte, werden angezeigt, je nach dem Wert, der im Feld **Framework\-Zielversion** im Dialogfeld **Neues Projekt hinzufügen** ausgewählt wird.  Das `MaxFrameworkVersion`\-Element sollte weggelassen werden, es sei denn, es ist erforderlich, damit Vorlagen nicht versehentlich angezeigt werden, wenn sie mit aktuelleren Versionen von .NET Framework verwendet werden.  
  
## Beispiel  
 Im folgenden Beispiel werden die Metadaten für die Vorlage einer Standardklasse in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] veranschaulicht.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <MaxFrameworkVersion>3.5</MaxFrameworkVersion>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 In diesem Beispiel ist die maximale Version von .NET Framework, die für die von `MaxFrameworkVersion` dargestellte Vorlage erforderlich ist, 3.5.  Die oben stehende Vorlage wird nur angezeigt, wenn Sie entweder 3.0 oder 3.5 im Feld **Framework\-Zielversion** im Dialogfeld **Neues Projekt hinzufügen** auswählen.  
  
## Siehe auch  
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)