---
title: Assembly-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
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
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 987e46810aa8cfe51102d2940bf48d24fd6824cf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513803"
---
# <a name="assembly-element-visual-studio-templates"></a>Assembly-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Assembly-Element (Visual Studio-Vorlagen)](https://docs.microsoft.com/visualstudio/extensibility/assembly-element-visual-studio-templates).  
  
Gibt Informationen zu einer Assembly, die die Vorlage verwendet, um einen Verweis von dieser Assembly zu Projekten hinzuzufügen.  
  
 \<VSTemplate>  
 \<TemplateContent >  
 \<Verweise >  
 \<Verweis >  
 \<Assembly >  
  
## <a name="syntax"></a>Syntax  
  
```  
<Assembly> AssemblyName </Assembly>  
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
  
 Dieser Text gibt die Assembly zu einem Projekt hinzugefügt werden soll, wenn die Item-Vorlage instanziiert wird. Diese Assembly muss in einem der folgenden Arten angegeben werden:  
  
-   Als vollständige AssemblyName. Zum Beispiel:  
  
    ```  
    <Assembly>  
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.  
    </Assembly>  
    ```  
  
-   Als einfachen Text-Verweis. Zum Beispiel:  
  
    ```  
    <Assembly> System </Assembly>  
    ```  
  
## <a name="remarks"></a>Hinweise  
 `Assembly` ist ein erforderliches untergeordnetes Element von `Reference`.  
  
 Die `Reference`, `References,` und `Assembly` Elemente können nur verwendet werden, in der VSTEMPLATE-Dateien, die eine `Type` -Attributwert `Item`.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die `TemplateContent` Element einer Elementvorlage. Dieser XML-Code fügt Verweise auf die Assemblys "System.dll" und "System.Data.dll" hinzu.  
  
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

