---
title: ButtonText-Element | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ef22471d20df5582fec96c8a685029a1d475a4a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184563"
---
# <a name="buttontext-element"></a>ButtonText-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Feld können Sie den Text angeben, der in verschiedenen Menüs angezeigt wird. Standardmäßig wird das- `ButtonText` Element in Menü Controllern angezeigt. Das- `ButtonText` Element wird auch der Standardwert, wenn die anderen Textfelder leer sind. Das `ButtonText` Element darf nicht leer sein, auch wenn die anderen Textfelder angegeben werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
<ButtonText>My Command</ButtonText>  
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
|[Strings-Element](../extensibility/strings-element.md)|Gruppiert Textelemente, wie z `ButtonText` `CommandName` . b. und.|  
  
## <a name="text-value"></a>Textwert  
 Der Textwert des- `ButtonText` Elements stellt den Text bereit, der für Menü Elemente, Combos und andere Benutzeroberflächen Elemente (UI) angezeigt wird, die über sichtbaren Text verfügen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
