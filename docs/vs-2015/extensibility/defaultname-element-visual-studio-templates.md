---
title: DefaultName-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords:
- DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bc3a18c47b78a312f3bca3762cc4ff3d658a70e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185290"
---
# <a name="defaultname-element-visual-studio-templates"></a>DefaultName-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gibt den Namen an, den das Visual Studio-Projekt System für das Projekt oder Element generiert, wenn es erstellt wird.  
  
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
  
 Dieser Text gibt den Standardnamen des Projekts oder Elements an.  
  
## <a name="remarks"></a>Bemerkungen  
 `DefaultName` ist ein optionales Element.  
  
 Bei-Projekten gibt dieses Element den Namen des Verzeichnisses an, in dem das Projekt auf dem Datenträger gespeichert wird. Für-Elemente wird der Dateiname der Quelldatei angegeben.  
  
 Wenn Sie ein Projekt oder Element erstellen, können Sie den Standardnamen mithilfe der Option **Name** ändern. diese Option ist entweder im Dialogfeld **Neues Projekt** oder im Dialogfeld **Neues Element hinzufügen** verfügbar.  
  
 Wenn Sie nicht möchten, dass das Projekt System den Standardnamen für das Projekt oder Element generiert, legen Sie das [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) -Element auf fest `False` .  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden die Metadaten für die Standardelement Vorlage für eine- [!INCLUDE[csprcs](../includes/csprcs-md.md)] Klasse veranschaulicht.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Schema Referenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt-und Element Vorlagen](../ide/creating-project-and-item-templates.md)
