---
title: 'Idiaframedata:: Get_program | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: ad54e98e2f05647a129158a10459cb111e199c99
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49859212"
---
# <a name="idiaframedatagetprogram"></a>IDiaFrameData::get_program
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  
1. Verschieben von Inhalt des Registers `ebp` zu `T0`.  
  
2. Hinzufügen `4` mit dem Wert im `T0` erzeugen eine Adresse, rufen Sie den Wert von dieser Adresse und speichern Sie den Wert im Register `eip`.  
  
3. Ruft den Wert aus der Adresse im `T0` und speichern Sie diesen Wert im Register `ebp`.  
  
4. Hinzufügen `8` mit dem Wert im `T0` und speichern Sie diesen Wert im Register `esp`.  
  
   Beachten Sie, dass die Programm-Zeichenfolge für die CPU und auf die Aufrufkonvention für die Funktion, die durch den aktuellen Stapelrahmen dargestellt eingerichtet ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)



