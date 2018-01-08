---
title: MaxFrameworkVersion-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c473b3253809c09f9ba0af90f7a0fed349dedb93
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion-Element (Visual Studio-Vorlagen)
Gibt die maximale Version von .NET Framework, die von der Vorlage erforderlich ist. Sie bestimmt, ob die Vorlage in angezeigt wird der **Vorlagen** Teil der **neues Projekt hinzufügen** (Dialogfeld), basierend auf dem Wert, der im ausgewählt ist die **Zielframeworkversion** im Feld der **neues Projekt hinzufügen** (Dialogfeld).  
  
 \<VSTemplate >  
 \<MaxFrameworkVersion >  
  
## <a name="syntax"></a>Syntax  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
 Keine  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie er angezeigt wird, entweder in der **neues Projekt** oder **neues Element hinzufügen** (Dialogfeld).|  
  
## <a name="text-value"></a>Textwert  
 Ein Textwert ist erforderlich.  
  
 Der Text muss die höchste Versionsnummer von .NET Framework, die die Vorlage nicht zulässig ist.  
  
## <a name="remarks"></a>Hinweise  
 `MaxFrameworkVersion` ist ein optionales Element. Das Element in der `TemplateData` Abschnitt der VSTEMPLATE-Datei dient als Filter für die **Vorlagen** Teil der **neues Projekt hinzufügen** (Dialogfeld). Nur Vorlagen, deren für .NET Framework sind, weniger als `MaxFrameworkVersion` Elementwerte angezeigt, auf Grundlage des Werts, der im ausgewählt ist die **Zielframeworkversion** im Feld der **neues Projekt hinzufügen**(Dialogfeld). Die `MaxFrameworkVersion` Element sollte weggelassen werden, es sei denn, es ist erforderlich, damit nicht versehentlich dazu führen, dass Vorlagen angezeigt wird, wenn sie durch neuere Versionen von .NET Framework verwendet werden.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Metadaten für einen Standard [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Klassenvorlage.  
  
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
  
 In diesem Beispiel die maximale Version des .NET Framework, die von der Vorlage erforderlich ist, die durch dargestellt `MaxFrameworkVersion`, 3.5 ist. Die oben stehende Vorlage wird nur angezeigt, wenn Auswahl 3.0 oder 3.5 in der **Zielframeworkversion** Feld der **neues Projekt hinzufügen** (Dialogfeld).  
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)