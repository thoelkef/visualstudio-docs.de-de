---
title: Reference-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c3d67fd19122e160159a6f636516dbca582fe31d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193835"
---
# <a name="reference-element-visual-studio-templates"></a>Reference-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gibt den Assemblyverweis an, der hinzugefügt wird, wenn das Element einem Projekt hinzugefügt wird.  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<References>  
 \<Reference>  
  
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
|[Stadtverordneten](../extensibility/assembly-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Gibt Informationen zu einer Assembly an, die von der Vorlage zum Hinzufügen eines Verweises auf diese Assembly zu Projekten verwendet wird. Es muss ein- `Assembly` Element in jedem-Element vorhanden sein `Reference` .|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Referenzen](../extensibility/references-element-visual-studio-templates.md)|Gruppiert die Assemblyverweise, die von der Vorlage Projekten hinzugefügt werden.|  
  
## <a name="remarks"></a>Bemerkungen  
 `Reference` ist ein erforderliches untergeordnetes Element von `References`.  
  
 Das `Reference` -Element und das- `References` Element können nur in. VSTEMPLATE-Dateien mit dem- `Type` Attribut Wert verwendet werden `Item` .  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht das-Element einer Element `TemplateContent` Vorlage. Dieses XML fügt Verweise auf die System.dll und System.Data.dll Assemblys hinzu.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Schema Referenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt-und Element Vorlagen](../ide/creating-project-and-item-templates.md)
