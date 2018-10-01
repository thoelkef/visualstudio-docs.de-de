---
title: TemplateID-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
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
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 688ec8e4db64ad36a189e0340c46f5b1a016f0d7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513898"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [TemplateID-Element (Visual Studio-Vorlagen)](https://docs.microsoft.com/visualstudio/extensibility/templateid-element-visual-studio-templates).  
  
Gibt einen Bezeichner für eine Elementvorlage, die in einer Gruppe von Elementvorlagen von kategorisiert ist die [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) Element.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<TemplateID >  
  
## <a name="syntax"></a>Syntax  
  
```  
<TemplateID> ... </TemplateID>  
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
 Ein `string` , das darstellt, eines Bezeichners für eine Elementvorlage, die in einer Gruppe von Elementvorlagen von kategorisiert ist die `TemplateGroupID` Element.  
  
## <a name="remarks"></a>Hinweise  
 `TemplateID` ist ein optionales Element.  
  
 Wenn eine VSTEMPLATE-Datei fehlt die `TemplateID` -Element, das [Name](../extensibility/name-element-visual-studio-templates.md) Element wird als Bezeichner für die Vorlage verwendet.  
  
 Der Wert des der `TemplateID` Element dient zusammen mit der projektsystemregistrierung (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects\\) Filterung von Vorlagen, die in angezeigt werden. die **neues Element hinzufügen** Das Dialogfeld.  
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)

