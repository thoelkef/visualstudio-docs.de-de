---
title: IDiaPropertyStorage::ReadMultiple | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b8be22e2a855f19c412725833fa18e182ebff6d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904043"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
Liest die angegebenen Eigenschaften aus der aktuellen Gruppe der Eigenschaft.  
  
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
 [in] Die Anzahl der in der angegebenen Eigenschaften der `rgpspec` Array. Falls der Wert NULL ist, wird die Methode gibt keine Eigenschaften zurück, aber gibt zurück, `S_OK` als einen Erfolgscode.  
  
 `rgpspec`  
 [in] Ein Array von Eigenschaften, die gelesen werden. Eigenschaften können entweder durch eine Eigenschafts-ID oder durch eine optionale Zeichenfolgenname angegeben werden. Es ist nicht erforderlich, um Eigenschaften in einer bestimmten Reihenfolge im Array anzugeben. Das Array kann doppelte Eigenschaften, was zu doppelten Eigenschaftswerten bei der Rückgabe für einfache Eigenschaften enthalten. Nicht-Simple-Eigenschaften sollten Zurückgeben der Zugriff verweigert beim Versuch, die sie ein zweites Mal zu öffnen. Das Array kann eine Mischung von Eigenschaft-IDs und Zeichenfolgen-IDs enthalten. Dieses Array benötigen mindestens `cpspec` Anzahl von Eigenschaftswerten.  
  
 `rgvar`  
 [in, out] Ein Array von `PROPVARIANT` Strukturen (im Namespace Microsoft.VisualStudio.OLE.Interop) mit Werten für jede Eigenschaft gefüllt werden soll. Das Array muss mindestens `cpspec` Elemente in der Größe. Der Aufrufer muss es sich nicht um die Werte im Array zu initialisieren.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` Wenn mindestens eine der Eigenschaften wurde nicht gefunden. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Eigenschaft wurde nicht gefunden, den zugehörigen Eintrag in der `rgvar` Array enthält einen `VARIANT` mit dem Typ des `VT_EMPTY`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)