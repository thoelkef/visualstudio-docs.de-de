---
title: Sicherheit von Textvorlagen
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25815bcb7f027501fb849dcd29d14b040c24d7fa
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591969"
---
# <a name="security-of-text-templates"></a>Sicherheit von Textvorlagen
Für Text Vorlagen gelten die folgenden Sicherheitsaspekte:

- Text Vorlagen sind anfällig für willkürliche Code Einfügungen.

- Wenn der Mechanismus, mit dem der Host einen Direktivenprozessor findet, nicht sicher ist, könnte ein böswilliger Direktivenprozessor ausgeführt werden.

## <a name="arbitrary-code"></a>Beliebiger Code
 Wenn Sie eine Vorlage schreiben, können Sie jeden beliebigen Code innerhalb der \<# # > Tags platzieren. Dadurch kann beliebiger Code aus einer Textvorlage heraus ausgeführt werden.

 Stellen Sie sicher, dass Sie Vorlagen aus vertrauenswürdigen Quellen abrufen. Stellen Sie sicher, dass die Endbenutzer Ihrer Anwendung keine Vorlagen ausführen, die nicht aus vertrauenswürdigen Quellen stammen.

## <a name="malicious-directive-processor"></a>Schädlicher Direktivenprozessor
 Die Textvorlagen-Engine interagiert mit einem Transformations Host und einem oder mehreren direktivenprozessoren, um den Vorlagen Text in eine Ausgabedatei umzuwandeln. Weitere Informationen finden Sie [unter Text Template Transformation Process](../modeling/the-text-template-transformation-process.md).

 Wenn der Mechanismus, mit dem der Host einen Direktivenprozessor findet, nicht sicher ist, besteht das Risiko, dass ein böswilliger Direktivenprozessor ausgeführt wird. Der böswillige Direktivenprozessor könnte Code bereitstellen, der im `FullTrust` Modus ausgeführt wird, wenn die Vorlage ausgeführt wird. Wenn Sie einen benutzerdefinierten Transformations Host für Textvorlagen erstellen, müssen Sie einen sicheren Mechanismus (z. b. die Registrierung) verwenden, damit die Engine direktivenprozessoren finden kann.
