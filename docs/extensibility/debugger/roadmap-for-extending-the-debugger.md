---
title: Roadmap zum Erweitern des Debuggers | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e809eeb6a1a5d2c24368932713d69c7199b5af38
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713137"
---
# <a name="roadmap-for-extending-the-debugger"></a>Roadmap zum Erweitern des Debuggers
Diese Dokumentation enthält Anleitungs- [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] und Referenzinformationen [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]zum Erweitern des Debuggers um die .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Die Debugdokumentation enthält Beispiele, eine umfassende Referenz und mehrere repräsentative Szenarien, die typische Methoden zum Anpassen des Debuggers veranschaulichen.

 Der Compiler und seine Ausgabe bestimmen, was zum Einrichten des Debuggens in Ihrem Produkt erforderlich ist. Wenn Ihr Compiler:

- Zielt auf das systemeigene Windows-Betriebssystem ab und schreibt eine *. PDB-Datei* können Sie Programme mit dem nativen Code-Debugmodul (DE) debuggen, das in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]integriert ist. Sie müssen keinen DE- oder Ausdrucksevaluator implementieren. Der Ausdrucksauswertungwird wird für die Syntax der Programmiersprache C++ geschrieben.

- Erzeugt die MSIL-Ausgabe (Microsoft Intermediate Language), können Sie Programme mit dem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Debugmodul DE für verwalteten Code debuggen, das ebenfalls in integriert ist. Daher müssen Sie nur einen Ausdrucksbewerter implementieren. Ein Beispielausdrucksevaluator wird für Sie bereitgestellt. Weitere Informationen finden Sie in den folgenden Themen:

   [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [Auswerten von Ausdrücken](../../extensibility/debugger/evaluating-expressions.md)

   [Ausdrucksbewertungskontext](../../extensibility/debugger/expression-evaluation-context.md)

   [Ausdrucksauswertung im Unterbrechungsmodus](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [Schreiben eines Common Language Runtime-Ausdrucksevaluators](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- Zielt auf ein proprietäres Betriebssystem oder eine andere Laufzeitumgebung, müssen Sie Ihre eigene DE schreiben. Ein Tutorial, das eine einfache DE mit ATL COM erstellt, wird bereitgestellt. Weitere Informationen finden Sie in den folgenden Themen:

   [Erstellen eines benutzerdefinierten Debugmoduls](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [Tutorial: Erstellen eines Debugmoduls mit ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)

   [Implementieren eines Portlieferanten](../../extensibility/debugger/implementing-a-port-supplier.md)

   [Beispiele](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>Weitere Informationen
- [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
