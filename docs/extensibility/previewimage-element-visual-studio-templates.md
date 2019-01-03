---
title: PreviewImage-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <PreviewImage> Element (Visual Studio Templates)
- PreviewImage Element (Visual Studio Templates)
ms.assetid: d1796f20-523b-4e0d-8ac3-ca87f3b5a9b6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b0e2c2f5f4914fafbf37daa5fbc8a9218c8e0482
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913396"
---
# <a name="previewimage-element-visual-studio-templates"></a>PreviewImage-Element (Visual Studio-Vorlagen)
Gibt das Vorschaubild als Dateiname, für das Vorschaubild, die entweder in angezeigt werden die **neues Projekt** oder **neues Element hinzufügen** Dialogfeld.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<PreviewImage >  
  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie es angezeigt wird, entweder in der **neues Projekt** oder **neues Element hinzufügen** Dialogfeld.|  
  
## <a name="text-value"></a>Textwert  
 Ein Textwert ist erforderlich.  
  
 Der Text muss eine Zeichenfolge sein, die einen Dateinamen darstellt.  
  
## <a name="remarks"></a>Hinweise  
 `PreviewImage` ist ein optionales Element.  
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz zu Visual Studio-Vorlage](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)