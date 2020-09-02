---
title: TemplateID-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1a52b360994c53eef69ceafa45828ec1020be16
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186420"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gibt einen Bezeichner für eine Element Vorlage an, die vom [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) -Element in eine Gruppe von Element Vorlagen kategorisiert wird.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<TemplateID>  
  
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
 Ein `string` , der einen Bezeichner für eine Element Vorlage darstellt, der vom-Element in eine Gruppe von Element Vorlagen kategorisiert wird `TemplateGroupID` .  
  
## <a name="remarks"></a>Bemerkungen  
 `TemplateID` ist ein optionales Element.  
  
 Wenn eine VSTEMPLATE-Datei das `TemplateID` Element auslässt, wird das [Name](../extensibility/name-element-visual-studio-templates.md) -Element als Bezeichner für die Vorlage verwendet.  
  
 Der Wert des- `TemplateID` Elements wird zusammen mit der Projekt Systemregistrierung (HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\11.0\Projects \\ ) zum Filtern von Vorlagen verwendet, die im Dialogfeld **Neues Element hinzufügen** angezeigt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schema Referenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt-und Element Vorlagen](../ide/creating-project-and-item-templates.md)
