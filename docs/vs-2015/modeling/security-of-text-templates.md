---
title: Sicherheit von Text Vorlagen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
ms.assetid: 567a2383-7d43-4acc-af4a-cd70b7a0151e
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e24a90d4e7af351fc4ba5807d2af7830edede9cb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671217"
---
# <a name="security-of-text-templates"></a>Sicherheit von Textvorlagen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Für Text Vorlagen gelten die folgenden Sicherheitsaspekte:

- Text Vorlagen sind anfällig für willkürliche Code Einfügungen.

- Wenn der Mechanismus, mit dem der Host einen Direktivenprozessor findet, nicht sicher ist, könnte ein böswilliger Direktivenprozessor ausgeführt werden.

## <a name="arbitrary-code"></a>Beliebiger Code
 Wenn Sie eine Vorlage schreiben, können Sie jeden beliebigen Code innerhalb der \< # # > Tags platzieren. Dadurch kann beliebiger Code aus einer Textvorlage heraus ausgeführt werden.

 Stellen Sie sicher, dass Sie Vorlagen aus vertrauenswürdigen Quellen abrufen. Stellen Sie sicher, dass die Endbenutzer Ihrer Anwendung keine Vorlagen ausführen, die nicht aus vertrauenswürdigen Quellen stammen.

## <a name="malicious-directive-processor"></a>Schädlicher Direktivenprozessor
 Die Textvorlagen-Engine interagiert mit einem Transformations Host und einem oder mehreren direktivenprozessoren, um den Vorlagen Text in eine Ausgabedatei umzuwandeln. Weitere Informationen finden Sie [unter Text Template Transformation Process](../modeling/the-text-template-transformation-process.md).

 Wenn der Mechanismus, mit dem der Host einen Direktivenprozessor findet, nicht sicher ist, besteht das Risiko, dass ein böswilliger Direktivenprozessor ausgeführt wird. Der böswillige Direktivenprozessor könnte Code bereitstellen, der im `FullTrust` Modus ausgeführt wird, wenn die Vorlage ausgeführt wird. Wenn Sie einen benutzerdefinierten Transformations Host für Textvorlagen erstellen, müssen Sie einen sicheren Mechanismus (z. b. die Registrierung) verwenden, damit die Engine direktivenprozessoren finden kann.
