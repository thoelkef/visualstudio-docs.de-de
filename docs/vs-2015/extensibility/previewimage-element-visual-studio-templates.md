---
title: PreviewImage-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <PreviewImage> Element (Visual Studio Templates)
- PreviewImage Element (Visual Studio Templates)
ms.assetid: d1796f20-523b-4e0d-8ac3-ca87f3b5a9b6
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 90521b5ea05aae2f54e56f21b65933a93580da85
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194068"
---
# <a name="previewimage-element-visual-studio-templates"></a>PreviewImage-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gibt das Vorschaubild (als Dateiname) für das Vorschaubild an, das im Dialogfeld **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<PreviewImage>  
  
## <a name="syntax"></a>Syntax  
  
```  
<PreviewImage>"filename"</PreviewImage>  
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
  
 Der Text muss eine Zeichenfolge sein, die einen Dateinamen darstellt.  
  
## <a name="remarks"></a>Bemerkungen  
 `PreviewImage` ist ein optionales Element.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schema Referenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt-und Element Vorlagen](../ide/creating-project-and-item-templates.md)
