---
title: 'VsgDbg:: ~ VsgDbg (Destruktor) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c0ae3dd206953e728175f4479920861295feae00
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200300"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (Destruktor)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zerstört eine Instanz der `VsgDbg`-Klasse. Wenn Grafikinformationen aktiv aufgezeichnet werden, wird die Grafikprotokolldatei abgeschlossen und geschlossen, und die Ressourcen, die während der aktiven Erfassung der Grafikinformationen verwendet wurden, werden freigegeben.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
~VsgDbg();  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VsgDbg::VsgDbg (Konstruktor)](../debugger/vsgdbg-vsgdbg-constructor.md)
