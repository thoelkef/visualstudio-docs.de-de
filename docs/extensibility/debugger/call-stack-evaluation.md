---
title: Auswertung der Aufrufliste | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fa28460c2680a5301768c950eac39caefc5d1dae
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332472"
---
# <a name="call-stack-evaluation"></a>Auswertung der Aufrufliste
Um die Stapel-Frames der Aufrufliste im Unterbrechungsmodus anzuzeigen, müssen Sie implementieren die [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) Methode.

## <a name="methods-for-evaluation"></a>Methoden für die Evaluierung
 Für einen einfachen Debug-Engine (DE) gibt es möglicherweise nur ein Stapelrahmen entspricht. Um den Stapelrahmen im Unterbrechungsmodus untersuchen zu können, müssen Sie die folgenden Methoden der implementieren [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).

|Methode|Beschreibung|
|------------|-----------------|
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Ruft den Kontext des Codes für einen Stapelrahmen ab. Der Codekontext stellt den aktuellen Anweisungszeiger in einem Stapelrahmen dar.|
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Ruft den Dokumentenkontext für einen Stapelrahmen ab. Den Dokumentenkontext darstellt, die aktuelle Position im Quellcode für ein Stapelrahmen. Erforderlich für das Anzeigen des Quellcodes, wenn Sie in einem Programm angehalten werden.|

 Diese Methoden erfordern die Implementierung verschiedener Kontext sammlungsbezogene Schnittstellen und Methoden. Daher müssen Sie implementieren die [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) -Methode und die folgenden Methoden der [idebugdocumentcontext2 angegeben](../../extensibility/debugger/reference/idebugdocumentcontext2.md).

|Methode|Beschreibung|
|------------|-----------------|
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Ruft die Datei-Anweisungsbereich eines Dokuments Kontexts ab.|

 Zum Auflisten von Codekontexte müssen Sie alle Methoden des implementieren [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).

## <a name="see-also"></a>Siehe auch
- [Ausführung und Auswertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)