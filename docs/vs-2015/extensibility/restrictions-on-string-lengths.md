---
title: Einschränkungen für Zeichenfolgenlängen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aa5517445930b5d543148af68df7eeeb29fa8a22
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523557"
---
# <a name="restrictions-on-string-lengths"></a>Einschränkungen für die Längen von Zeichenfolgen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Einschränkungen für Zeichenfolgenlängen](https://docs.microsoft.com/visualstudio/extensibility/restrictions-on-string-lengths).  
  
Die Source-Plug-in-API schränkt die Längen der Zeichenfolgen, die in verschiedenen Funktionen verwendet.  
  
## <a name="string-length-values"></a>Länge-Zeichenfolgenwerten  
  
|Konstante|Wert|  
|--------------|-----------|  
|`SCC_NAME_LEN`|31|  
|`SCC_AUXLABEL_LEN`|31|  
|`SCC_USER_LEN`|31|  
|`SCC_PRJPATH_LEN`|300|  
  
> [!NOTE]
>  Länge schließt nicht das abschließende `null`. Schließen Sie andere Konstanten mit dem Suffix "_Größe" anstelle von "_LEN" Speicherplatz für das abschließende `null`.  
  
|Konstante|Wert|  
|--------------|-----------|  
|SCC_NAME_SIZE|32|  
|SCC_AUXLABEL_SIZE|32|  
|SCC_USER_SIZE|32|  
|SCC_PRJPATH_SIZE|301|  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)

