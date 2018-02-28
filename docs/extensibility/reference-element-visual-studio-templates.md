---
title: Verweisen Sie-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1006e85611044805c0f3bd1e0035595288a5b32d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="reference-element-visual-studio-templates"></a>Reference-Element (Visual Studio-Vorlagen)
Gibt den Assemblyverweis an, der hinzugefügt wird, wenn das Element einem Projekt hinzugefügt wird.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Verweise >  
 \<Verweis >  
  
## <a name="syntax"></a>Syntax  
  
```  
<Reference>  
    <Assembly> ... </Assembly>  
</Reference>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
 Keine  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Assembly](../extensibility/assembly-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Gibt Informationen zu einer Assembly, die die Vorlage verwendet, um einen Verweis von dieser Assembly zu Projekten hinzuzufügen. Es muss eine `Assembly` Element in jedem `Reference` Element.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Verweise](../extensibility/references-element-visual-studio-templates.md)|Gruppiert die Assemblyverweise, die von die Vorlage zu Projekten hinzugefügt.|  
  
## <a name="remarks"></a>Hinweise  
 `Reference` ist ein erforderliches untergeordnetes Element von `References`.  
  
 Die `Reference` und `References` Elemente können nur verwendet werden, in der VSTEMPLATE-Dateien, die über eine `Type` -Attributwert `Item`.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die `TemplateContent` Element einer Elementvorlage. Durch dieses XML werden Verweise auf die Assemblys "System.dll" und "System.Data.dll" hinzugefügt.  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)