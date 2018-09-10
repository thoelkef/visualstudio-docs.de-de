---
title: Einschränkungen für Zeichenfolgenlängen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5b3552a88f5a78b627e72e877758cf6b7d12de95
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638533"
---
# <a name="restrictions-on-string-lengths"></a>Einschränkungen der Zeichenfolge
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
 [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)