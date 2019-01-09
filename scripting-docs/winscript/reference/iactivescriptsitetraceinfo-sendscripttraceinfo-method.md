---
title: 'Iactivescriptsitetraceinfo:: Sendscripttraceinfo-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 0419e4c5-eb7c-45a3-b6dc-1a5e157d95f9
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f08a5cb0e7bd297dede85190ac694185e2fd795
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091623"
---
# <a name="iactivescriptsitetraceinfosendscripttraceinfo-method"></a>IActiveScriptSiteTraceInfo::SendScriptTraceInfo-Methode
Sendet Ablaufverfolgungsinformationen, die den Ereignistyp, Kontext und die skriptanweisung enthält.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SendScriptTraceInfo(     [in] SCRIPTTRACEINFO stiEventType,     [in] GUID guidContextID,     [in] DWORD dwScriptContextCookie,     [in] LONG lScriptStatementStart,     [in] LONG lScriptStatementEnd,     [in] DWORD64 dwReserved );   
```  
  
#### <a name="parameters"></a>Parameter  
 `stiEventType`  
 Der Ereignistyp.  
  
 `guidContextId`  
 Die GUID des Kontexts.  
  
 `dwScriptContextCookie`  
 Das Cookie des Kontexts.  
  
 `lScriptStatementStart`  
 Die Position des Anfangs der skriptanweisung.  
  
 `lScriptStatementEnd`  
 Die Position des Endes der skriptanweisung.  
  
 `dwReserved`  
 Reserviert.