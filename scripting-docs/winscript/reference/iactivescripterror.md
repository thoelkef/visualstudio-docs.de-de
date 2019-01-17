---
title: IActiveScriptError | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 540a4a338ae8ebfcacae66b1890075c20bdee086
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347098"
---
# <a name="iactivescripterror"></a>IActiveScriptError
Ein Objekt, das diese Schnittstelle implementiert wird, übergeben die [IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md) -Methode auf, wenn die Skript-Engine einen nicht behandelten Fehler auftritt. Der Host ruft dann die Methoden für dieses Objekt zum Abrufen von Informationen über den Fehler, die aufgetreten sind.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptError::GetExceptionInfo](../../winscript/reference/iactivescripterror-getexceptioninfo.md)|Ruft Informationen zu einem Fehler ab.|  
|[IActiveScriptError::GetSourcePosition](../../winscript/reference/iactivescripterror-getsourceposition.md)|Ruft die Position im Quellcode, in denen ein Fehler aufgetreten ist.|  
|[IActiveScriptError::GetSourceLineText](../../winscript/reference/iactivescripterror-getsourcelinetext.md)|Ruft ab, die Zeile in der Quelldatei, in denen ein Fehler aufgetreten ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Schnittstellen](../../winscript/reference/active-script-interfaces.md)