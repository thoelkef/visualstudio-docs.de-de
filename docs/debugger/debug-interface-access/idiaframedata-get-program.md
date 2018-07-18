---
title: 'Idiaframedata:: Get_program | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2c78c6f1c2c6e8368efd86dc3ffa03a021e46da3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459596"
---
# <a name="idiaframedatagetprogram"></a>IDiaFrameData::get_program
Ruft die Programm-Zeichenfolge, die verwendet wird, um den Registersatz vor dem Aufruf an die aktuelle Funktion zu berechnen.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Die Programm-Zeichenfolge zurückgegeben.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die Programm-Zeichenfolge ist eine Sequenz von Makros, die den Prolog gewahrt interpretiert wird. Ein typische Stapelrahmen kann z. B. die Programm-Verbindungszeichenfolge verwenden `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`. Das Format ist die umgekehrte Polnisch-Notation, in denen die Operatoren führen Sie die Operanden. `T0` Stellt eine temporäre Variable auf dem Stapel dar. In diesem Beispiel führt die folgenden Schritte aus:  
  
1.  Verschieben von Inhalt des Registers `ebp` auf `T0`.  
  
2.  Hinzufügen `4` auf den Wert in `T0` erzeugen eine Adresse, rufen Sie den Wert von dieser Adresse und den Wert in der Registrierung speichern `eip`.  
  
3.  Rufen Sie den Wert von der Adresse, die in gespeicherten `T0` und speichern Sie diesen Wert im Register `ebp`.  
  
4.  Hinzufügen `8` auf den Wert in `T0` und speichern Sie diesen Wert im Register `esp`.  
  
 Beachten Sie, dass die Programm-Zeichenfolge für die CPU und in die Aufrufkonvention für die Funktion, die durch den aktuellen Stapelrahmen dargestellt eingerichtet ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)