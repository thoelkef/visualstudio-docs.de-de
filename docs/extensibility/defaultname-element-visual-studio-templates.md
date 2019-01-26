---
title: DefaultName-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords:
- DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f8dfd0a5efd302b64130fc2ed029b94d4396d4e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54927079"
---
# <a name="defaultname-element-visual-studio-templates"></a>DefaultName-Element (Visual Studio-Vorlagen)
Gibt den Namen, den das Projektsystem von Visual Studio generiert wird, wird für das Projekt oder Element an, bei der Erstellung.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<DefaultName>  
  
## <a name="syntax"></a>Syntax  
  
```  
<DefaultName>  
    Default Project Name  
</DefaultName>  
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
  
 Dieser Text gibt den Standardnamen des Projekts oder Elements.  
  
## <a name="remarks"></a>Hinweise  
 `DefaultName` ist ein optionales Element.  
  
 Für Projekte gibt dieses Element den Namen des Verzeichnisses, in dem das Projekt auf dem Datenträger gespeichert. Für Elemente gibt er den Dateinamen der Quelldatei an.  
  
 Wenn Sie ein Projekt oder Element erstellen, können Sie ändern, den Standardwert mit der **Name** Option in entweder die **neues Projekt** im Dialogfeld oder **neues Element hinzufügen** Das Dialogfeld.  
  
 Wenn Sie nicht, dass das Projektsystem, um den Standardnamen für das Projekt oder Element zu generieren möchten, legen Sie die [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) Element `False`.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt die Metadaten für die standard-Elementvorlage für eine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Klasse.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <DefaultName>MyClass.cs</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz zu Visual Studio-Vorlage](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)