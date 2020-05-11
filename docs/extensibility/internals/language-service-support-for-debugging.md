---
title: Sprachdienst-Support für das Debuggen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c80e8e1f584b1728f342cb596b689f6a22c9297
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707433"
---
# <a name="language-service-support-for-debugging"></a>Sprachdienstunterstützung für das Debuggen
Ein Sprachdienst kann Features bereitstellen, die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> einen Debugger über die Schnittstelle unterstützen. Zu diesen Funktionen gehören das Überprüfen von Haltepunkten und das Bereitstellen einer Liste von Ausdrücken für das **Fenster "Autos".**

 Sie benötigen jedoch einen Ausdrucksevaluator, um Ihre Sprache zu debuggen. Der Ausdrucksauswertungswert ist für das Auswerten von Ausdrücken zum Erstellen von Werten während des Debuggens verantwortlich. Informationen zum Implementieren von CLR-Expressionsevaluatoren finden Sie unter:

- [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [Beispiel für managed Expression Evaluator](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>Compilerausgabe
 Der Typ des Compilers bestimmt, was Sie tun müssen, um das Debuggen für Ihre Sprache zu implementieren. Wenn Ihr Compiler auf das Windows-Betriebssystem abzielt und eine PDB-Datei schreibt, können Sie Programme mit dem systemeigenen Codedebuggingmodul debuggen, das in Visual Studio integriert ist. Wenn Ihr Compiler Microsoft Intermediate Language (MSIL) erstellt, können Sie Programme mit dem Debugmodul für verwalteten Code debuggen, das ebenfalls in Visual Studio integriert ist. Wenn Ihr Compiler auf ein proprietäres Betriebssystem oder eine andere Laufzeitumgebung abzielt, müssen Sie ein eigenes Debugmodul schreiben.

 Weitere Informationen zum Implementieren des Debuggens für Ihre Sprache finden Sie unter [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) im Visual Studio Debugging SDK.
