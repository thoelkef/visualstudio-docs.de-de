---
title: Beispielimplementierung von Locals | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b70e0f9091d40ed6b5fc44934606f42ccd84b21
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713073"
---
# <a name="sample-implementation-of-locals"></a>Beispielimplementierung von Locals
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Ausdrucksevaluatoren finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Beispiel für den Auswertungsbeispiel für managed expression evaluator](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Im Folgenden finden Sie eine Übersicht darüber, wie Visual Studio die Locals für eine Methode aus dem Ausdrucksevaluator (EE) abruft:

1. Visual Studio ruft die [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) des Debugmoduls (DE) auf, um ein [IDebugProperty2-Objekt](../../extensibility/debugger/reference/idebugproperty2.md) abzuruft, das alle Eigenschaften des Stapelrahmens, einschließlich der Locals, darstellt.

2. `IDebugStackFrame2::GetDebugProperty`ruft [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) auf, um ein Objekt abzuruft, das die Methode beschreibt, innerhalb derer der Haltepunkt aufgetreten ist. Die DE stellt einen Symbolanbieter ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), eine Adresse ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) und einen Binder ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)) zur Verfügung.

3. `IDebugExpressionEvaluator::GetMethodProperty`ruft [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) mit `IDebugAddress` dem angegebenen Objekt auf, um ein [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) abzuerhalten, das die Methode darstellt, die die angegebene Adresse enthält.

4. Die `IDebugContainerField` Schnittstelle wird für die [IDebugMethodField-Schnittstelle](../../extensibility/debugger/reference/idebugmethodfield.md) abgefragt. Es ist diese Schnittstelle, die Zugriff auf die Lokalen der Methode gibt.

5. `IDebugExpressionEvaluator::GetMethodProperty`instanziiert eine Klasse `CFieldProperty` (im Beispiel genannt), `IDebugProperty2` die die Schnittstelle ausführt, um die Locals der Methode darzustellen. Das `IDebugMethodField` Objekt wird `CFieldProperty` in diesem `IDebugSymbolProvider`Objekt `IDebugAddress`zusammen `IDebugBinder` mit den , und Objekten platziert.

6. Wenn `CFieldProperty` das Objekt initialisiert wird, wird `IDebugMethodField` [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) für das Objekt aufgerufen, um eine [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) Struktur zu erhalten, die alle anzeigebaren Informationen über die Methode selbst enthält.

7. `IDebugExpressionEvaluator::GetMethodProperty`gibt `CFieldProperty` das Objekt `IDebugProperty2` als Objekt zurück.

8. Visual Studio ruft [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) für das zurückgegebene `IDebugProperty2` Objekt mit dem Filter `guidFilterLocalsPlusArgs`auf, der ein [IEnumDebugPropertyInfo2-Objekt](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) zurückgibt, das die Locals der Methode enthält. Diese Enumeration wird durch Aufrufe von [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) und [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)ausgefüllt.

9. Visual Studio ruft [Next](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) auf, um eine [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) Struktur für jeden lokalen Ort zu erhalten. Diese Struktur enthält einen `IDebugProperty2` Zeiger auf eine Schnittstelle für ein Lokales.

10. Visual Studio ruft [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) für jeden Lokalen auf, um den Namen, den Wert und den Typ des Lokalen abzusondern. Diese Informationen werden im Fenster **"Lokale"** angezeigt.

## <a name="in-this-section"></a>In diesem Abschnitt
 [GetMethodProperty implementieren](../../extensibility/debugger/implementing-getmethodproperty.md) Beschreibt eine Implementierung von [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).

 [Aufzählen von Einheimischen](../../extensibility/debugger/enumerating-locals.md) Beschreibt, wie das Debugmodul (DE) einen Aufruf zum Aufzählen lokaler Variablen oder Argumente ausführt.

 [Lokale Eigenschaften abrufen](../../extensibility/debugger/getting-local-properties.md) Beschreibt, wie die DE einen Aufruf zum Abrufen des Namens, typs und des Werts eines oder mehrerer Locals ausführt.

 [Lokale Werte abrufen](../../extensibility/debugger/getting-local-values.md) Erläutert das Abrufen des Werts des lokalen Objekts, das die Dienste eines Binderobjekts erfordert, das vom Auswertungskontext angegeben wird.

 [Bewerten Sie die Einheimischen](../../extensibility/debugger/evaluating-locals.md) Erläutert, wie Locals ausgewertet werden.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Evaluierungskontext](../../extensibility/debugger/evaluation-context.md) Stellt die Argumente bereit, die übergeben werden, wenn die DE den Ausdrucksevaluator (EE) aufruft.

 [MyCEE-Beispiel](https://msdn.microsoft.com/library/624a018b-9179-402f-9d48-3aec87b48f4f) Veranschaulicht einen Implementierungsansatz zum Erstellen eines Ausdrucksevaluators für die MyC-Sprache.

## <a name="see-also"></a>Weitere Informationen
- [Anzeigen von Einheimischen](../../extensibility/debugger/displaying-locals.md)
