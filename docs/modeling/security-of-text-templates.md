---
title: Sicherheit von Textvorlagen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- text templates, security
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5c6b8d64e02562887b2bc438943fdfe7be3b2e1c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
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