---
title: IDiaPropertyStorage::ReadMultiple | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ffa66117095ef73ac9d25ce8117431f03ba0ad57
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
Liest eine angegebene Eigenschaften nicht mit der aktuellen Eigenschaft.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cpspec`  
 [in] Anzahl der in der angegebenen Eigenschaften der `rgpspec` Array. Wenn der Wert 0 ist, die Methode keine Eigenschaften zurückgegeben, aber gibt zurück `S_OK` als einen Erfolgscode.  
  
 `rgpspec`  
 [in] Ein Array von Eigenschaften gelesen werden. Eigenschaften können entweder durch eine Eigenschafts-ID oder durch eine optionale Zeichenfolgenname angegeben werden. Es ist nicht notwendig, dass Eigenschaften in einer bestimmten Reihenfolge in das Array angeben. Das Array kann doppelte Eigenschaften, wodurch doppelte Werte bei der Rückgabe für einfache Eigenschaften enthalten. Nicht einfach Eigenschaften sollte zurückgeben Zugriff verweigert, bei einem Versuch, ein zweites Mal zu öffnen. Das Array kann eine Kombination von Eigenschaften-IDs und Zeichenfolgen-IDs enthalten. Dieses Array benötigen mindestens `cpspec` Anzahl von Eigenschaftswerten.  
  
 `rgvar`  
 [in, out] Ein Array von `PROPVARIANT` Strukturen (im Namespace Microsoft.VisualStudio.OLE.Interop), die mit Werten für jede Eigenschaft ausgefüllt werden. Das Array muss mindestens `cpspec` Elemente in der Größe. Der Aufrufer muss es sich nicht um die Werte im Array zu initialisieren.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`. Gibt `S_FALSE` , wenn eine oder mehrere der Eigenschaften nicht gefunden wurde. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Eigenschaft wurde nicht gefunden, den zugehörigen Eintrag in der `rgvar` Array enthält ein `VARIANT` mit dem Typ des `VT_EMPTY`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)