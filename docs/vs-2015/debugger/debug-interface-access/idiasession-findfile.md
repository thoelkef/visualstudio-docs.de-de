---
title: 'IDiaSession:: FindFile | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e791bc09ba3dd4f1811c650926eadb0f7f0462a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431640"
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft Quelldateien nach dem Kompilieren und dem Namen ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT findFile (   
   IDiaSymbol*           pCompiland,  
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSourceFiles** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pCompiland`  
 in Ein [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt, das das kompiand darstellt, das als Kontext für die Suche verwendet werden soll. Legen Sie diesen Parameter auf fest, `NULL` um Quelldateien in allen Kompilierungen zu suchen.  
  
 `name`  
 in Gibt den Namen der Quelldatei an, die abgerufen werden soll. Legen Sie diesen Parameter auf fest, `NULL` damit alle Quelldateien abgerufen werden.  
  
 `option`  
 in Gibt die Vergleichs Optionen an, die auf die Namenssuche angewendet werden. Werte aus der Enumeration-Enumeration von [NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) können allein oder in Kombination verwendet werden.  
  
 `ppResult`  
 vorgenommen Gibt ein [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) -Objekt zurück, das eine Liste der abgerufenen Quelldateien enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="example"></a>Beispiel  
  
```cpp#  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions-Enumeration](../../debugger/debug-interface-access/namesearchoptions.md)
