---
title: SortOrder-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a6473e867655974f42f41a276b8becfd12fbab7a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder-Element (Visual Studio-Vorlagen)
Gibt einen Wert an, die zum Anordnen der Vorlage gegenüber anderen Vorlagen in der gleichen Kategorie verwendet wird, wie er im entweder enthalten die **neues Projekt** oder **neues Element hinzufügen** (Dialogfeld).  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<SortOrder >  
  
## <a name="syntax"></a>Syntax  
  
```  
<SortOrder> ... </SortOrder>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|  
  
## <a name="text-value"></a>Textwert  
 Ein Textwert ist erforderlich.  
  
 Eine `integer` , die den Sortierreihenfolgenwert darstellt.  
  
## <a name="remarks"></a>Hinweise  
 `SortOrder` ist ein optionales Element. Der Standardwert ist 100, und alle Werte müssen ein Vielfaches von 10 sein.  
  
 Die `SortOrder` Element wird für benutzerdefinierte Vorlagen ignoriert. Alle benutzerdefinierten Vorlagen sind alphabetisch sortiert.  
  
 Vorlagen, die mit niedriger Reihenfolge Sortierwerten haben angezeigt werden, entweder in der **neues Projekt** oder **neues Element hinzufügen** Dialogfeld vor Vorlagen, die hohe sortieren reihenfolgenwerte aufweisen.  
  
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
        <SortOrder>290</SortOrder>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 In diesem Beispiel wird die `SortOrder` Element ist relativ hoch. Ist es wahrscheinlich, dass andere [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Elementvorlagen müssen eine `SortOrder` Wert niedriger ist als `290` und wird angezeigt, bevor dieser Vorlage in der **neues Element** (Dialogfeld).  
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)