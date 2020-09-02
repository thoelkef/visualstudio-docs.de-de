---
title: 'IDiaFrameData:: get_program | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d87f5c7fda25a901d44b9f511b9a92eb4471f845
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180003"
---
# <a name="idiaframedataget_program"></a>IDiaFrameData::get_program
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die Programm Zeichenfolge ab, die verwendet wird, um den Register Satz vor dem aufgerufenen der aktuellen Funktion zu berechnen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Gibt die Programm Zeichenfolge zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt zurück, `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Programm Zeichenfolge ist eine Sequenz von Makros, die zum Erstellen des Prologs interpretiert wird. Beispielsweise kann ein typischer Stapel Rahmen die Programm Zeichenfolge verwenden `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="` . Das Format ist die umgekehrte polnische Notation, bei der die Operatoren den Operanden folgen. `T0` stellt eine temporäre Variable im Stapel dar. In diesem Beispiel werden die folgenden Schritte ausgeführt:  
  
1. Verschieben Sie den Inhalt von Register `ebp` nach `T0` .  
  
2. Fügen Sie `4` dem Wert in hinzu, `T0` um eine Adresse zu erhalten, den Wert von dieser Adresse zu erhalten und den Wert in Register zu speichern `eip` .  
  
3. Sie erhalten den Wert aus der Adresse, die in gespeichert ist `T0` , und speichern diesen Wert in Register `ebp` .  
  
4. Fügen Sie `8` dem Wert in hinzu, `T0` und speichern Sie diesen Wert in Register `esp` .  
  
   Beachten Sie, dass die Programm Zeichenfolge für die CPU und die Aufruf Konvention spezifisch ist, die für die durch den aktuellen Stapel Rahmen dargestellte Funktion eingerichtet ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
