---
title: 'IDiaSession:: findinlineelinesbyaddr | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: bb70e408-eed1-4c9c-b5b1-44323125f48b
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2b35850367ef4bcc4e49cc3d6e76b41a2e9f4cd7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151698"
---
# <a name="idiasessionfindinlineelinesbyaddr"></a>IDiaSession::findInlineeLinesByAddr
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft eine Enumeration ab, die es einem Client ermöglicht, die Zeilennummerinformationen aller Funktionen, die direkt oder indirekt durch das angegebene übergeordnete Symbol eingebunden sind, zu durchlaufen und innerhalb des angegebenen Adress Bereichs enthalten sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT findInlineeLinesByAddr (   
   IDiaSymbol*           parent,   DWORD                 isect,   DWORD                 offset,   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `parent`  
 in Ein `IDiaSymbol` Objekt, das das übergeordnete Element darstellt.  
  
 `isect`  
 in Gibt die Abschnitts Komponente der Adresse an.  
  
 `offset`  
 in Gibt die Offset Komponente der Adresse an.  
  
 `length`  
 in Gibt den Adressbereich in Byte an, der mit dieser Abfrage abgedeckt werden soll.  
  
 `ppResult`  
 vorgenommen Enthält ein- `IDiaEnumLineNumbers` Objekt, das die Liste der abgerufenen Zeilennummern enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
