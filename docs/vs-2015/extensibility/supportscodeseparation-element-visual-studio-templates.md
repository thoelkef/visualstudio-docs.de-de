---
title: SupportsCodeSeparation-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation
helpviewer_keywords:
- SupportsCodeSeparation element [Visual Studio Templates]
- <SupportsCodeSeparation> element [Visual Studio Templates]
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 492b77cf0eaa7f656de0df5ee2724945be980364
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516381"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>SupportsCodeSeparation-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [SupportsCodeSeparation-Element (Visual Studio-Vorlagen)](https://docs.microsoft.com/visualstudio/extensibility/supportscodeseparation-element-visual-studio-templates).  
  
Gibt an, ob die **Code in eigener Datei platzieren** Kontrollkästchen in aktiviert ist die **neues Element hinzufügen** im Dialogfeld.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<SupportsCodeSeparation >  
  
## <a name="syntax"></a>Syntax  
  
```  
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie es in einem angezeigt. die **neues Projekt** oder **neues Element** Dialogfeld.|  
  
## <a name="text-value"></a>Textwert  
 Ein Textwert ist erforderlich.  
  
 Der Text muss entweder `true` oder `false`gibt an, unabhängig davon, ob die **Code in eigener Datei platzieren** Kontrollkästchen in aktiviert ist die **neues Element hinzufügen** im Dialogfeld.  
  
## <a name="remarks"></a>Hinweise  
 `SupportsCodeSeparation` ist ein optionales Element. Der Standardwert ist `false`.  
  
 Die `SupportsCodeSeparation` -Element ist nur verfügbar für Web-Elementvorlagen.  
  
 Codetrennung und das Code-Behind-Seitenmodell, können Sie das Markup in eine Datei und den Programmcode in einer anderen Datei zu speichern. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] und anderen verwenden Sie dieses Modell.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird zum Anzeigen der **Code in eigener Datei platzieren** Option.  
  
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
        <SupportsCodeSeparation>true</SupportsCodeSeparation>  
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

