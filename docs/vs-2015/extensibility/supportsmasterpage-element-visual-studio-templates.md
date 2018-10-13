---
title: SupportsMasterPage-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsMasterPage
helpviewer_keywords:
- <SupportsMasterPage> element [Visual Studio Templates]
- SupportsMasterPage element [Visual Studio Templates]
ms.assetid: ce877a6a-9bba-4fd9-92fb-0a8dfec9e75b
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1886121e7dd92e14fca48e220899d84c7cbc5632
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49191554"
---
# <a name="supportsmasterpage-element-visual-studio-templates"></a>SupportsMasterPage-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gibt an, ob das die **Masterseite auswählen** Kontrollkästchen ist aktiviert, auf die **neues Element hinzufügen** Dialogfeld.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<SupportsMasterPage >  
  
## <a name="syntax"></a>Syntax  
  
```  
<SupportsMasterPage> true/false </SupportsMasterPage>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gibt an, Daten, die kategorisiert die Vorlage und definiert, wie es in angezeigt. die **neues Projekt** oder **neues Element** Dialogfeld.|  
  
## <a name="text-value"></a>Textwert  
 Ein Textwert ist erforderlich.  
  
 Der Text muss entweder `true` oder `false`gibt an, unabhängig davon, ob die **Masterseite auswählen** Kontrollkästchen ist aktiviert, auf die **neues Element hinzufügen** im Dialogfeld.  
  
## <a name="remarks"></a>Hinweise  
 `SupportsMasterPage` ist ein optionales Element. Der Standardwert ist `false`.  
  
 Die `SupportsMasterPage` -Element ist nur verfügbar für Web-Elementvorlagen.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt die Metadaten für ein Webprojekt, die Unterstützung für eine Masterseite enthält.  
  
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
        <SupportsMasterPage>true</SupportsMasterPage>  
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

