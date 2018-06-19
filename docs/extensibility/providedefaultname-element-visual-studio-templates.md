---
title: ProvideDefaultName-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fbe291c838d006bea62450f7e397cde7e5d09ee3
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2018
ms.locfileid: "34454375"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>ProvideDefaultName-Element (Visual Studio-Vorlagen)
Gibt an, ob die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projektsystem generiert einen Standardnamen für die Vorlage in der **neues Element hinzufügen** oder **neues Projekt** (Dialogfeld).  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<ProvideDefaultName >  
  
## <a name="syntax"></a>Syntax  
  
```  
<ProvideDefaultName> true/false </ProvideDefaultName>  
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
  
 Der Text muss entweder `true` oder `false`, der angibt, ob ein Standardname für die Vorlage in generieren die **neues Element hinzufügen** oder **neues Projekt** (Dialogfeld).  
  
## <a name="remarks"></a>Hinweise  
 `ProvideDefaultName` ist ein optionales Element. Der Standardwert ist `true`.  
  
 Wenn die `ProvideDefaultName` Element ist `false`, die **Namen** Feldern der **neues Element hinzufügen** und **neues Projekt** Dialogfelder enthalten den Wert `<Enter_name>`.  
  
 Verwenden der [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) Elements, geben Sie den Standardnamen des Projekts oder Element in der **neues Element hinzufügen** und **neues Projekt** Dialogfelder. Bei den Wert des der `ProvideDefaultName` Element ist `true`, nicht angegeben die `DefaultName` -Element für Projekte füllt das Dialogfeld mit der Name der Vorlage, d. h. den Wert aus der [Namen](../extensibility/name-element-visual-studio-templates.md) Element.
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird die `ProvideDefaultName` Element `false`.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProvideDefaultName>false</ProvideDefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
