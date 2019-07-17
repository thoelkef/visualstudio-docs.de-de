---
title: SccEndBatch-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 986056b1f5202c2fb94d27a8792ed3b0fe308944
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200147"
---
# <a name="sccendbatch-function"></a>SccEndBatch-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion ist einen Batch von Quellcodeverwaltungsvorgänge abgeschlossen. Diese Batches können nicht geschachtelt werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
SCCRTN SccEndBatch(void);  
```  
  
#### <a name="parameters"></a>Parameter  
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
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
