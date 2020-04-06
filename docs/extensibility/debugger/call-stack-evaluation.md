---
title: Call-Stack-Evaluierung | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5557d7eae0ffe54b0f01f1f9e95935d71455229
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739179"
---
# <a name="call-stack-evaluation"></a>Anrufstapelauswertung
Um die Stapelrahmen der Aufrufliste während des Unterbrechungsmodus anzuzeigen, müssen Sie die [EnumFrameInfo-Methode](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) implementieren.

## <a name="methods-for-evaluation"></a>Methoden zur Bewertung
 Für ein einfaches Debugmodul (DE) gibt es möglicherweise nur einen Stapelrahmen. Um den Stapelrahmen während des Unterbrechungsmodus zu untersuchen, müssen Sie die folgenden Methoden von [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)implementieren.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Ruft den Codekontext für einen Stapelrahmen ab. Der Codekontext stellt den aktuellen Anweisungszeiger in einem Stapelrahmen dar.|
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Ruft den Dokumentkontext für einen Stapelrahmen ab. Der Dokumentkontext stellt die aktuelle Position im Quellcode für einen Stapelrahmen dar. Erforderlich für die Anzeige des Quellcodes, wenn Sie in einem Programm angehalten werden.|

 Diese Methoden erfordern die Implementierung mehrerer kontextbezogener Schnittstellen und Methoden. Daher müssen Sie die [GetDocumentContext-Methode](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) und die folgenden Methoden von [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md)implementieren.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Ruft den Dateianweisungsbereich eines Dokumentkontexts ab.|

 Um Codekontexte aufzuzählen, müssen Sie alle Methoden von [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)implementieren.

## <a name="see-also"></a>Weitere Informationen
- [Ausführungskontrolle und Zustandsbewertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)
