---
title: CustomParameters-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4c09d320b1a9185e79e36d54ff0363219d3dabc6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099801"
---
# <a name="customparameters-element-visual-studio-templates"></a>CustomParameters-Element (Visual Studio-Vorlagen)
Gruppiert die benutzerdefinierten Parameter ab, auf dem Vorlagen-Assistenten übergeben werden, wenn der Assistent sorgt für die Parameter-Ersetzungen.  
  
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
 Im folgende Beispiel wird gezeigt, wie mehrere benutzerdefinierte Parameter in einer Vorlage verwendet wird. Wenn ein Projekt oder Element aus einer Vorlage mit den folgenden benutzerdefinierten Parametern, alle Instanzen der erstellt wird `$color1$` und `$color2$` in der Vorlage die Dateien ersetzt werden, mit `Red` und `Blue`zugeordnet.  
  
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