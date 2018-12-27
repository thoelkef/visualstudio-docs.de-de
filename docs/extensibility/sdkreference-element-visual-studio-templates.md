---
title: SDKReference-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 72c8b352-0b7a-42b3-ba5d-2a2d1e90c34b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4ac32f5cae1e2e31f40a7d49c861757aec43fa5b
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2018
ms.locfileid: "53562008"
---
# <a name="sdkreference-element-visual-studio-templates"></a>SDKReference-Element (Visual Studio-Vorlagen)
Gibt an, dass die Elementvorlage eine SDK-Referenz verwendet.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<VSTemplate>      
    <TemplateContent>          
        <References>              
            <Reference>  
                <SDKReference>SDKname</SDKReference>  
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
|[Verweis](../extensibility/reference-element-visual-studio-templates.md)|Gibt den Assemblyverweis an, der hinzugefügt wird, wenn das Element einem Projekt hinzugefügt wird.|  
  
## <a name="text-value"></a>Textwert  
 Ein Textwert ist erforderlich.  
  
## <a name="remarks"></a>Hinweise  
 Dieser Text gibt die SDK-Referenz an, die einem Projekt beim Instanziieren der Elementvorlage hinzugefügt werden soll.  
  
```xml  
<VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">   
    <TemplateData> . . . </TemplateData>   
    <TemplateContent>   
        <References>   
            <Reference>   
                <SDKReference>Microsoft Visual C++ Runtime Package, Version=11.0.0.0</SDKReference>  
...  
```  
  
## <a name="see-also"></a>Siehe auch  
 [References-Element (Visual Studio-Vorlagen)](../extensibility/references-element-visual-studio-templates.md)   
 [Reference-Element (Visual Studio-Vorlagen)](../extensibility/reference-element-visual-studio-templates.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)