---
title: ButtonText-Element | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 35973241d1f68965680332fb3baf7c9b13c1bbcc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790213"
---
# <a name="buttontext-element"></a>ButtonText-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dieses Feld ermöglicht die Angabe der Text erscheint in verschiedenen Menüs. In der Standardeinstellung die `ButtonText` Element wird im Menücontroller angezeigt. Die `ButtonText` Element wird auch die Standardeinstellung, wenn die anderen Textfelder leer sind. Die `ButtonText` Element darf nicht leer sein, auch wenn die anderen Textfelder angegeben werden.  
  
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
|[Strings-Element](../extensibility/strings-element.md)|Text-Elemente, wie z. B. gruppiert `ButtonText` und `CommandName`.|  
  
## <a name="text-value"></a>Textwert  
 Der Textwert, der die `ButtonText` -Element stellt den Text, der angezeigt wird, für Menüelemente, Combos und andere Elemente der Benutzeroberfläche (UI), die sichtbaren Text bereit.  
  
## <a name="see-also"></a>Siehe auch  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

