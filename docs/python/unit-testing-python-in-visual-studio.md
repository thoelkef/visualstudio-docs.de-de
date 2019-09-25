---
title: Komponententest für Python-Code
description: Einrichten von Unittests für Python-Code in Visual Studio, um die Features des Test-Explorers zum Ermitteln, Ausführen und Debuggen von Tests in vollem Umfang zu nutzen.
ms.date: 09/18/2019
ms.topic: include
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 09c67ace9db36cb8ee3d94296d339b62849e3c94
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254195"
---
# <a name="set-up-unit-testing-for-python-code"></a>Einrichten von Komponententests für Python-Code

Komponententests sind Codeelemente, die andere Codeeinheiten in einer Anwendung testen, in der Regel isolierte Funktionen, Klassen usw. Wenn eine Anwendung alle Unittests besteht, können Sie sich zumindest darauf verlassen, dass die Funktionalität im Detail korrekt ist.

In Python werden Komponententests ausgiebig zum Überprüfen von Szenarien beim Entwurf eines Programms verwendet. Die Python-Unterstützung in Visual Studio umfasst das Ermitteln, Ausführen und Debuggen von Unittests im Kontext Ihres Entwicklungsprozesses, sodass sie nicht separat ausgeführt werden müssen.

Dieser Artikel enthält eine kurze Übersicht über die Komponententestfunktionen in Visual Studio mit Python. Weitere Informationen zu Komponententests im Allgemeinen finden Sie unter [Komponententest für Code](../test/unit-test-your-code.md).

::: moniker range="vs-2017"

[!include[Testing Python code](includes/vs-2017/unit-testing-python.md)]

::: moniker-end

::: moniker range=">= vs-2019"

[!include[Testing Python code](includes/vs-2019/unit-testing-python.md)]

::: moniker-end