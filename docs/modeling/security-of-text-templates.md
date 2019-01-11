---
title: Sicherheit von Textvorlagen
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: bb5ad4348d681a2b7bc59c588bb74e0a27813e73
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53820811"
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