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
ms.technology: vs-ide-modeling
ms.openlocfilehash: 71052a0d4120a74269f2aa05412230284271e574
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947520"
---
# <a name="security-of-text-templates"></a>Sicherheit von Textvorlagen
Textvorlagen haben die folgenden Sicherheitsaspekte:

-   Textvorlagen sind anfällig für das Einfügen von beliebigem Code.

-   Wenn der Mechanismus, den vom Host verwendet werden, finden Sie einen Direktivenprozessor nicht sicher ist, könnte ein böswilliger Direktivenprozessor ausgeführt werden.

## <a name="arbitrary-code"></a>Beliebigen Codes
 Wenn Sie eine Vorlage erstellen, können Sie put Code innerhalb der \<## > RFID-Transponder. Dies kann beliebigen Code innerhalb einer Textvorlage ausgeführt werden.

 Achten Sie darauf, dass Sie die Vorlagen aus vertrauenswürdigen Quellen abrufen. Stellen Sie sicher, dass die Warnung, die Endbenutzer von der Anwendung nicht in Vorlagen ausführen, die nicht aus vertrauenswürdigen Quellen stammen.

## <a name="malicious-directive-processor"></a>Böswillige Direktivenprozessor
 Das Textvorlagenmodul interagiert mit einem Transformationshost und eine oder mehrere Direktivenprozessoren zum Transformieren des Vorlage-Texts in eine Ausgabedatei. Weitere Informationen finden Sie unter [der Textvorlagen-Transformationsprozess](../modeling/the-text-template-transformation-process.md).

 Wenn der Mechanismus, den vom Host verwendet werden, finden Sie einen Direktivenprozessor nicht sicher ist, wird das Risiko der Ausführung eines böswilligen Direktivenprozessors ausgeführt. Der böswillige Direktivenprozessor könnte Code, der ausgeführt wird, in bereitstellen `FullTrust` Modus aus, wenn die Vorlage ausgeführt wird. Wenn Sie einen benutzerdefinierten Textvorlagen-Transformationshost erstellen, müssen Sie einen sicheren Mechanismus, wie z. B. die Registrierung für das Modul für die Suche nach Direktivenprozessoren verwenden.