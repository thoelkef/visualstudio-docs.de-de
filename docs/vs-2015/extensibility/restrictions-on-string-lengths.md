---
title: Einschränkungen für Zeichenfolgenlängen | Microsoft-Dokumentation
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
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f600ef47526c3b2d9e703781c8f20ddb563dcf4a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206224"
---
# <a name="restrictions-on-string-lengths"></a>Einschränkungen für die Längen von Zeichenfolgen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

