---
title: SupportsLanguageDropDown-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown
helpviewer_keywords:
- SupportsLanguageDropDown element [Visual Studio Templates]
- <SupportsLanguageDropDown> element [Visual Studio Templates]
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 53703d6178c81758650fdd00aada0a5952734caa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160488"
---
# <a name="supportslanguagedropdown-element-visual-studio-templates"></a>SupportsLanguageDropDown-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gibt an, ob die Web-Elementvorlage für mehrere Programmiersprachen identisch ist, und ob die **Sprache** Option aktiviert ist, auf die **neues Element hinzufügen** Dialogfeld.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<SupportsLanguageDropDown>  
  
## <a name="syntax"></a>Syntax  
  
```  
<SupportsLanguageDropDown> true/false </SupportsLanguageDropDown>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
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
  
 Der Text muss entweder `true` oder `false`gibt an, unabhängig davon, ob die **Sprache** Option ist verfügbar der **neues Element hinzufügen** Dialogfeld.  
  
## <a name="remarks"></a>Hinweise  
 `SupportsLanguageDropDown` ist ein optionales Element. Der Standardwert ist `false`.  
  
 Die `SupportsLanguageDropDown` -Element ist nur verfügbar für Web-Elementvorlagen.  
  
 Wenn der Wert für dieses Element, um festgelegt ist `true`, und klicken Sie dann die Item-Vorlage für alle Programmiersprachen identisch ist und die **Sprache** aktiviert ist die **neues Element hinzufügen** im Dialogfeld. Diese Option können Sie die Programmiersprache des neuen Elements an, die Sie aus der Vorlage erstellen möchten.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird zum Anzeigen der **Sprache** Dropdown-Option.  
  
```  
<VSTemplate Version="3.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
        <SupportsLanguageDropDown>true</SupportsLanguageDropDown>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="WebApplication.webproj">  
            <ProjectItem>icon.ico</ProjectItem>  
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>  
            <ProjectItem>Default.aspx.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
