---
title: SccEndBatch Funktion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ec549b5bb0a6c48946edf59f0ab1423cea0ac704
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138222"
---
# <a name="sccendbatch-function"></a>SccEndBatch-Funktion
Diese Funktion wird einen Batch von Quellcodeverwaltungsvorgänge abgeschlossen. Diese Batches können nicht geschachtelt werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccEndBatch(void);  
```  
  
#### <a name="parameters"></a>Parameter  
 Keine  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Batches von Vorgängen, die erfolgreich abgeschlossen.|  
|SCC_E_UNKNOWNERROR|Unspezifischen Fehlers.|  
  
## <a name="remarks"></a>Hinweise  
 Source Control Batches werden verwendet, um die gleichen Quellcodeverwaltungsvorgänge über mehrere Projekte oder mehrere Kontexte hinweg ausführen. Batches können verwendet werden, um redundante Dialogfelder, über die Benutzeroberfläche während eines Vorgangs im Batchmodus zu vermeiden. Die [SccBeginBatch](../extensibility/sccbeginbatch-function.md) und die `SccEndBatch` Funktion als Paar verwendet werden, um Anfang und Ende eines Vorgangs anzugeben. Sie sind nicht schachtelbar.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)