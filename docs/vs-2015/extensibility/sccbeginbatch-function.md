---
title: SccBeginBatch-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 264d9057bf4f17281d6d8a16ed3a6794004e0e21
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961946"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion wird eine Batch-Sequenz von Quellcodeverwaltungsvorgänge gestartet. Die [SccEndBatch](../extensibility/sccendbatch-function.md) wird aufgerufen, um den Batch beenden. Diese Batches können nicht geschachtelt werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
SCCRTN SccBeginBatch(void);  
```  
  
#### <a name="parameters"></a>Parameter  
 Keine  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Batches von Vorgängen wurde erfolgreich gestartet.|  
|SCC_E_UNKNOWNERROR|Nicht spezifischen Fehler.|  
  
## <a name="remarks"></a>Hinweise  
 Source-Control-Batches werden verwendet, um die gleichen Vorgänge über mehrere Projekte oder mehrere Kontexte auszuführen. Batches können verwendet werden, um redundante projektbezogene Dialogfeldern auf die Benutzeroberfläche während eines Vorgangs im Batchmodus zu vermeiden. Die `SccBeginBatch` Funktion und die [SccEndBatch](../extensibility/sccendbatch-function.md) dienen als Funktionspaar Anfang und Ende eines Vorgangs an. Sie sind nicht schachtelbar. `SccBeginBatch` Legt ein Flag, der angibt, dass ein Batchvorgang ausgeführt wird.  
  
 Während ein Batchvorgangs aktiviert ist, sollte das Quellcodeverwaltungs-Plug-in höchstens ein Dialogfeld für Fragen an den Benutzer vorhanden und die Antwort in diesem Dialogfeld auf alle nachfolgenden Operationen anwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)
