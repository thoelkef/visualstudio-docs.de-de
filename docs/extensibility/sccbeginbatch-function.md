---
title: SccBeginBatch Funktion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5350484294d02356301839e38b97bea1d40ec27c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch-Funktion
Diese Funktion wird eine Batch-Sequenz von Quellcodeverwaltungsvorgänge gestartet. Die [SccEndBatch](../extensibility/sccendbatch-function.md) wird aufgerufen, um den Batch beenden. Diese Batches können nicht geschachtelt werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccBeginBatch(void);  
```  
  
#### <a name="parameters"></a>Parameter  
 Keine  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Batches von Vorgängen wurde erfolgreich gestartet.|  
|SCC_E_UNKNOWNERROR|Unspezifischen Fehlers.|  
  
## <a name="remarks"></a>Hinweise  
 Source Control Batches werden verwendet, um über mehrere Projekte oder mehrere Kontexte hinweg die gleichen Vorgänge auszuführen. Batches können verwendet werden, um redundante pro Projekt Dialogfelder, über die Benutzeroberfläche während eines Vorgangs im Batchmodus zu vermeiden. Die `SccBeginBatch` Funktion und die [SccEndBatch](../extensibility/sccendbatch-function.md) werden als Funktionspaar verwendet, um Anfang und Ende eines Vorgangs anzugeben. Sie sind nicht schachtelbar. `SccBeginBatch` setzt ein Flag gibt an, dass ein Batch ausgeführt wird.  
  
 Während ein Batchvorgangs aktiviert ist, sollte das Quellsteuerelement-Plug-in präsentieren darf höchstens ein Dialogfeld für jede Frage an den Benutzer und die Antwort in diesem Dialogfeld auf alle nachfolgenden Vorgänge gelten.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)