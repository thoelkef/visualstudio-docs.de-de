---
title: 'Idiaframedata:: Get_program | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6daf5262552d056a6ac2d46a092fe94ec7510b15
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47521005"
---
# <a name="idiaframedatagetprogram"></a>IDiaFrameData::get_program
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idiaframedata:: Get_program](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaframedata-get-program).  
  
Ruft ab, die Programm-Zeichenfolge, die zum Berechnen der Registrierung festlegen, bevor der Aufruf von der aktuellen Funktion verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Die Programm-Zeichenfolge zurückgegeben.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die Programm-Zeichenfolge ist eine Sequenz von Makros, die den Prolog gewahrt interpretiert wird. Beispielsweise können ein typisches Stapelrahmen die Programm-Zeichenfolge `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`. Das Format ist reverse Polnisch-Notation, in dem die Operatoren mit Operanden folgen. `T0` Stellt eine temporäre Variable auf dem Stapel dar. In diesem Beispiel führt die folgenden Schritte aus:  
  
1.  Verschieben von Inhalt des Registers `ebp` zu `T0`.  
  
2.  Hinzufügen `4` mit dem Wert im `T0` erzeugen eine Adresse, rufen Sie den Wert von dieser Adresse und speichern Sie den Wert im Register `eip`.  
  
3.  Ruft den Wert aus der Adresse im `T0` und speichern Sie diesen Wert im Register `ebp`.  
  
4.  Hinzufügen `8` mit dem Wert im `T0` und speichern Sie diesen Wert im Register `esp`.  
  
 Beachten Sie, dass die Programm-Zeichenfolge für die CPU und auf die Aufrufkonvention für die Funktion, die durch den aktuellen Stapelrahmen dargestellt eingerichtet ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)



