---
title: CustomParameter-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords: CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8b2380a585b1c428516e1578587c64b93d5b1d4e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="customparameter-element-visual-studio-templates"></a>CustomParameter-Element (Visual Studio-Vorlagen)
Enthält eine benutzerdefinierte Parametername und der Wert, der verwendet wird, wenn ein Projekt oder Element aus der Vorlage erstellt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Name`|Erforderlich. Der Name des Parameters. Das Format für Parameter lautet $*Namen*$.|  
|`Value`|Erforderlich. Der Ersatzwert für den Parameter.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Gruppiert die benutzerdefinierten Parameter ab, auf dem Vorlagen-Assistenten übergeben werden, wenn der Assistent sorgt für die Parameter-Ersetzungen.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Vorlage enthält `CustomParameter` Elemente, die jede Instanz die `Name` Attribut wird durch ersetzt die `Value` -Attribut in die erstellten Projekt oder Element-Dateien.  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird gezeigt, wie mehrere benutzerdefinierte Parameter in einer Vorlage verwendet wird. Wenn ein Projekt oder Element aus einer Vorlage mit den folgenden benutzerdefinierten Parametern, alle Instanzen der erstellt wird `$color1$` und `$color2$` in der Vorlage die Dateien ersetzt werden, mit `Red` und `Blue`zugeordnet.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [CustomParameters-Element (Visual Studio-Vorlagen)](../extensibility/customparameters-element-visual-studio-templates.md)   
 [Vorlagenparameter](../ide/template-parameters.md)   
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)