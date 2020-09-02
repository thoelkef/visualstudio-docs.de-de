---
title: Maxframeworkversion-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194328"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gibt die maximale Version der .NET Framework an, die für die Vorlage erforderlich ist. Es bestimmt, ob die Vorlage im Dialogfeld Neues Projekt hinzufügen im Abschnitt **Vorlagen** des Dialog Felds **Neues Projekt hinzufügen** angezeigt wird. Dies basiert auf dem Wert, der im Dialogfeld **Neues Projekt hinzufügen** im Feld **Ziel Framework-Version** ausgewählt ist.  
  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie Sie im Dialogfeld **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|  
  
## <a name="text-value"></a>Textwert  
 Ein Textwert ist erforderlich.  
  
 Der Text muss die höchste Versionsnummer des .NET Framework sein, der von der Vorlage zugelassen wird.  
  
## <a name="remarks"></a>Bemerkungen  
 `MaxFrameworkVersion` ist ein optionales Element. Das-Element im- `TemplateData` Abschnitt der VSTEMPLATE-Datei fungiert als Filter für den Abschnitt **Vorlagen** des Dialog Felds **Neues Projekt hinzufügen** . Nur Vorlagen, deren .NET Framework Anforderungen kleiner als `MaxFrameworkVersion` Element Werte sind, werden auf der Grundlage des Werts angezeigt, der im Dialogfeld **Neues Projekt hinzufügen** im Feld **Ziel Framework-Version** ausgewählt ist. Das `MaxFrameworkVersion` Element sollte weggelassen werden, es sei denn, es ist erforderlich, sodass Vorlagen nicht versehentlich angezeigt werden, wenn Sie mit neueren Versionen der .NET Framework verwendet werden.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden die Metadaten für eine Standard [!INCLUDE[csprcs](../includes/csprcs-md.md)] Klassen Vorlage veranschaulicht.  
  
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
  
 In diesem Beispiel ist die maximale Version der .NET Framework, die für die Vorlage erforderlich ist, die durch dargestellt wird, `MaxFrameworkVersion` 3,5. Die obige Vorlage wird nur angezeigt, wenn Sie im Dialogfeld **Neues Projekt hinzufügen** im Feld **Ziel Framework-Version** entweder 3,0 oder 3,5 auswählen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schema Referenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt-und Element Vorlagen](../ide/creating-project-and-item-templates.md)
