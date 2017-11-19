---
title: Sicherheit von Textvorlagen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, security
ms.assetid: 567a2383-7d43-4acc-af4a-cd70b7a0151e
caps.latest.revision: "23"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 7c99f0a519ec62a2b9946baba072b0256a78697a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
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