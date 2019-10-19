---
title: Iactivescripterror | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptError interface
ms.assetid: c8e0288d-38ff-4145-a7e3-f8cdfb72eefe
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca4d3fe5ff90fc0d116814771308fa599052dba9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576899"
---
# <a name="iactivescripterror"></a>IActiveScriptError
Ein Objekt, das diese Schnittstelle implementiert, wird an die [iactivescriptsite:: onscripterror](../../winscript/reference/iactivescriptsite-onscripterror.md) -Methode übergeben, wenn die Skript-Engine einen nicht behandelten Fehler feststellt. Der Host ruft dann Methoden für dieses Objekt auf, um Informationen zum aufgetretenen Fehler zu erhalten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptError::GetExceptionInfo](../../winscript/reference/iactivescripterror-getexceptioninfo.md)|Ruft Informationen zu einem Fehler ab.|  
|[IActiveScriptError::GetSourcePosition](../../winscript/reference/iactivescripterror-getsourceposition.md)|Ruft den Speicherort im Quellcode ab, an dem ein Fehler aufgetreten ist.|  
|[IActiveScriptError::GetSourceLineText](../../winscript/reference/iactivescripterror-getsourcelinetext.md)|Ruft die Zeile in der Quelldatei ab, in der ein Fehler aufgetreten ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Schnittstellen](../../winscript/reference/active-script-interfaces.md)