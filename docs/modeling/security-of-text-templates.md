---
title: Sicherheit von Textvorlagen
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d9906f3b8af624e1761b73c3338bad98b263aa9e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55957181"
---
# <a name="security-of-text-templates"></a>Sicherheit von Textvorlagen
Textvorlagen haben die folgenden Sicherheitsaspekte:

-   Textvorlagen sind anfällig für Einfügen von beliebigem Code.

-   Wenn der Mechanismus, den vom Host verwendet wird, finden Sie einen anweisungsprozessor nicht sicher ist, könnte ein böswilliger Direktivenprozessor ausgeführt werden.

## <a name="arbitrary-code"></a>Beliebigen Code
 Wenn Sie eine Vorlage schreiben, Sie können Code einfügen, alle innerhalb der \<## > Tags. Dies kann beliebigen Code innerhalb einer Textvorlage ausgeführt werden.

 Achten Sie darauf, dass Sie Vorlagen aus vertrauenswürdigen Quellen abrufen. Stellen Sie sicher, dass die Warnung, die Endbenutzer Ihrer Anwendung nicht auf Vorlagen ausführen können, die nicht von vertrauenswürdigen Quellen stammen.

## <a name="malicious-directive-processor"></a>Böswillige Direktivenprozessor
 Das Textvorlagenmodul interagiert mit einem Transformationshost "und"-anweisungsprozessoren für eine oder mehrere ", um den Text der Vorlage in eine Ausgabedatei zu transformieren. Weitere Informationen finden Sie unter [das Textvorlagen-Transformationsprozess](../modeling/the-text-template-transformation-process.md).

 Wenn der Mechanismus, den vom Host verwendet wird, finden Sie einen anweisungsprozessor nicht sicher ist, wird das Risiko der Ausführung eines böswilligen Direktivenprozessors ausgeführt. Der böswillige Direktivenprozessor kann Code, der ausgeführt wird, in bereitstellen `FullTrust` Modus aus, wenn die Vorlage ausgeführt wird. Wenn Sie eine benutzerdefinierte Textvorlagen-Transformationshost erstellen, müssen Sie einen sicheren Mechanismus, wie z. B. der Registrierung für die Engine für anweisungsprozessoren suchen verwenden.