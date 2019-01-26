---
title: SccEndBatch-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fdc86d9b93d25a758e5321832b6bd4d98c171147
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54982376"
---
# <a name="sccendbatch-function"></a>SccEndBatch-Funktion
Diese Funktion ist einen Batch von Quellcodeverwaltungsvorgänge abgeschlossen. Diese Batches können nicht geschachtelt werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccEndBatch(void);  
```  
  
## <a name="parameters"></a>Parameter  
 Keine  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Batches von Vorgängen, die erfolgreich abgeschlossen.|  
|SCC_E_UNKNOWNERROR|Nicht spezifischen Fehler.|  
  
## <a name="remarks"></a>Hinweise  
 Source-Control-Batches werden verwendet, um die gleichen Quellcodeverwaltungsvorgänge über mehrere Projekte oder mehrere Kontexte auszuführen. Batches können verwendet werden, um redundante Dialogfelder über die Benutzeroberfläche während eines Vorgangs im Batchmodus zu vermeiden. Die [SccBeginBatch](../extensibility/sccbeginbatch-function.md) und `SccEndBatch` Funktion dienen als ein paar Anfang und Ende eines Vorgangs an. Sie sind nicht schachtelbar.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellen-Steuerelement-Plug-in-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)