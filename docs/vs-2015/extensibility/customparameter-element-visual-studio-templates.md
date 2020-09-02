---
title: CustomParameter-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59bfec972750a4f893d1cb8b7cf08710bcca761a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555959"
---
# <a name="customparameter-element-visual-studio-templates"></a>CustomParameter-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Enthält einen benutzerdefinierten Parameternamen und-Wert, der verwendet werden soll, wenn ein Projekt oder ein Element aus der Vorlage erstellt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|`Name`|Erforderlich. Der Name des Parameters. Das Format für Parameter ist "$*Name*$".|  
|`Value`|Erforderlich. Der Ersatzwert für den Parameter.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Gruppiert die benutzerdefinierten Parameter, die an den Vorlagen-Assistenten übergeben werden, wenn der Assistent Parameter Ersetzungen vornimmt.|  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn eine Vorlage `CustomParameter` Elemente enthält, wird jede Instanz, die das Attribut enthält, durch `Name` das- `Value` Attribut in den erstellten Projekt-oder Element Dateien ersetzt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie mehrere benutzerdefinierte Parameter in einer Vorlage verwendet werden. Wenn ein Projekt oder Element aus einer Vorlage mit den folgenden benutzerdefinierten Parametern erstellt wird, werden alle Instanzen von `$color1$` und `$color2$` in den Vorlagen Dateien durch `Red` `Blue` bzw. ersetzt.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CustomParameters-Element (Visual Studio-Vorlagen)](../extensibility/customparameters-element-visual-studio-templates.md)   
 [Vorlagen Parameter](../ide/template-parameters.md)   
 [Schema Referenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
