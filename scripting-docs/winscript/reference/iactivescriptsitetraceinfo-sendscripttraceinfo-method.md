---
title: 'Iactivescriptsitetraceinfo:: Sendscripttraceinfo-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 0419e4c5-eb7c-45a3-b6dc-1a5e157d95f9
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c2b444afa22e38694166f7d7522dbe6d0d3774d4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992279"
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