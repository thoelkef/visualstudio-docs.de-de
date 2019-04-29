---
title: CustomParameters-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f7be98415a4ab0d6d5c2d00891680e2959e93fe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62555937"
---
# <a name="customparameters-element-visual-studio-templates"></a>CustomParameters-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gruppiert die benutzerdefinierten Parameter ab, die Vorlagen-Assistenten übergeben werden, wenn der Assistent Parameter Ersetzungen vornimmt.  
  
## <a name="syntax"></a>Syntax  
  
```  
<CustomParameters>  
    <CustomParameter/>  
    <CustomParameter/>  
</CustomParameters>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
 Keine  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Enthält eine benutzerdefinierte Parametername und der Wert, der verwendet wird, wenn ein Projekt oder Element aus der Vorlage erstellt wird. Es kann keine oder mehrere `CustomParameter`-Elemente in einem `CustomParameters`-Element geben.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Gibt den Inhalt der Vorlage.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie mehrere benutzerdefinierte Parameter in einer Vorlage zu verwenden. Wenn ein Projekt oder Element aus einer Vorlage mit den folgenden benutzerdefinierten Parametern, alle Instanzen der erstellt wird `$color1$` und `$color2$` in der Vorlage die Dateien ersetzt werden, mit `Red` und `Blue`bzw.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [CustomParameter-Element (Visual Studio-Vorlagen)](../extensibility/customparameter-element-visual-studio-templates.md)   
 [Vorlagenparameter](../ide/template-parameters.md)   
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
