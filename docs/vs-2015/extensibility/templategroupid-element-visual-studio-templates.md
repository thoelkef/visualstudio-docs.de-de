---
title: TemplateGroupID-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
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
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9955b577db6f2e1ab7c34ed7b97b242d7b763c72
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792202"
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gibt an, in welcher Art von Projekt eine Elementvorlage angezeigt wird. Dieses Element ist erheblich, wenn [ShowByDefault (Visual Studio-Vorlagen)](../extensibility/showbydefault-visual-studio-templates.md) nastaven NA hodnotu `false`. Wenn [ShowByDefault (Visual Studio-Vorlagen)](../extensibility/showbydefault-visual-studio-templates.md) nastaven NA hodnotu `true`, und klicken Sie dann eine Elementvorlage in allen Projekttypen verfügbar ist.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<TemplateGroupID >  
  
## <a name="syntax"></a>Syntax  
  
```  
<TemplateGroupID> ... </TemplateGroupID>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|  
  
## <a name="text-value"></a>Textwert  
 Ein Textwert ist erforderlich.  
  
 Der Text gibt einen Bezeichner für eine Kategorie von Elementvorlagen an.  
  
## <a name="remarks"></a>Hinweise  
 `TemplateGroupID` ist ein Element.  
  
 Der Wert des der `TemplateGroupID` Element dient zusammen mit der projektsystemregistrierung (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Versionsnummer >* \Projects\\) Filterung von Vorlagen, die in angezeigt werden. die **neues Element hinzufügen** Dialogfeld.  
  
|Visual C++-Wert|Bedeutung|  
|------------------------|-------------|  
|VC-systemeigen|Für systemeigene Projekte verwendet. Auch die Standardeinstellung, wenn ein Projekttyp nicht bestimmt werden kann.|  
|VC-verwaltet|Für verwaltete Projekte (/clr) verwendet.|  
|VC-Windows|Für alle Projekte verwendet, die auf die Windows-Plattform abzielen (systemeigen/verwaltet/Speicher).|  
|WinRT-systemeigen-UAP|Für Windows 10-Store-Projekte verwendet.|  
|CodeSharing-systemeigen|Für freigegebene Elementprojekte verwendet.|  
|WinRT-systemeigen-6.3|Für Windows 8.1-Store-Projekte verwendet.|  
|WinRT-systemeigen-Phone-6.3|Für Windows Phone 8.1-Projekte verwendet.|  
|WinRT-systemeigen|Für Windows 8.0-Store-Projekte verwendet.|  
|VC-Android|Für Android-Projekte verwendet.|  
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)

