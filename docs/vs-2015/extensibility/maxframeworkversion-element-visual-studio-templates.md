---
title: MaxFrameworkVersion-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4a1c27e42574429dbb6b2eaeb140db484bf29db5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194328"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gibt die maximale Version von .NET Framework, die von der Vorlage erforderlich sind. Es bestimmt, ob die Vorlage, in angezeigt wird der **Vorlagen** Teil der **neues Projekt hinzufügen** basierend auf dem Wert, der ausgewählt wird im Dialogfeld der **Zielframeworkversion** im Feld der **neues Projekt hinzufügen** Dialogfeld.  
  
 \<VSTemplate>  
 \<MaxFrameworkVersion>  
  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie es angezeigt wird, entweder in der **neues Projekt** oder **neues Element hinzufügen** Dialogfeld.|  
  
## <a name="text-value"></a>Textwert  
 Ein Textwert ist erforderlich.  
  
 Der Text muss die höchste Versionsnummer von .NET Framework, die von der Vorlage zulässig ist.  
  
## <a name="remarks"></a>Hinweise  
 `MaxFrameworkVersion` ist ein optionales Element. Das Element in der `TemplateData` Abschnitt der VSTEMPLATE-Datei dient als Filter für die **Vorlagen** Teil der **neues Projekt hinzufügen** Dialogfeld. Nur Vorlagen, deren .NET Framework-Anforderungen sind, kleiner als `MaxFrameworkVersion` Elementwerte angezeigt, basierend auf dem Wert, der ausgewählt wird die **Zielframeworkversion** im Feld der **neues Projekt hinzufügen**Dialogfeld. Die `MaxFrameworkVersion` Element sollte ausgelassen werden, es sei denn, es ist erforderlich, damit nicht versehentlich dazu führen, dass Vorlagen angezeigt wird, wenn sie mit neueren Versionen von .NET Framework verwendet werden.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt die Metadaten für die Standard [!INCLUDE[csprcs](../includes/csprcs-md.md)] -Klassenvorlage.  
  
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
  
 In diesem Beispiel ist die maximale Version des .NET Framework, die von der Vorlage erforderlich ist, der durch dargestellt `MaxFrameworkVersion`, ist 3.5. In der obige Vorlage erscheint nur, wenn Sie 3.0 oder 3.5 im Auswählen der **Framework-Zielversion** im Feld der **neues Projekt hinzufügen** Dialogfeld.  
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
