---
title: 'VsgDbg:: ~ VsgDbg (Destruktor) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 16fce161dc1c01797a67fe8d104c26ce603a4b76
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (Destruktor)
Zerstört eine Instanz der `VsgDbg`-Klasse. Wenn Grafikinformationen aktiv aufgezeichnet werden, wird die Grafikprotokolldatei abgeschlossen und geschlossen, und die Ressourcen, die während der aktiven Erfassung der Grafikinformationen verwendet wurden, werden freigegeben.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
~VsgDbg();  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VsgDbg::VsgDbg (Konstruktor)](vsgdbg-vsgdbg-constructor.md)