---
title: 'Gewusst wie: Erstellen einer Arbeitsaufgabe für einen Fehler in verwaltetem Code'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- managed code, creating work items for code defects
- code analysis, creating work items
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: b251970bfd57b31842e1573e2e156e11a517c81a
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279473"
---
# <a name="how-to-create-a-work-item-for-a-managed-code-defect"></a>Gewusst wie: Erstellen einer Arbeitsaufgabe für einen Fehler in verwaltetem Code

Sie können die Arbeit Element-Überwachungsfunktion mit Protokolldatei für eine Arbeitsaufgabe aus in Visual Studio verwenden. Um dieses Feature verwenden zu können, muss Ihr Projekt Teil eines Azure DevOps-Projekts in [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)].

## <a name="to-create-a-work-item-for-managed-code-defect"></a>Um ein Arbeitselement für Fehler in verwaltetem Code zu erstellen.

1. In der **Codeanalyse** Fenster, wählen Sie die Warnung.

2. Wählen Sie **Aktionen**, wählen Sie dann **Arbeitsaufgabe erstellen** , und wählen Sie den Typ des zu erstellenden Arbeitselements.

     Ein neues Arbeitselement erstellt für Sie um die Fehler anzugeben.

## <a name="to-create-a-work-item-for-multiple-managed-code-defects"></a>Um ein Arbeitselement für mehrere Fehlern in verwaltetem Code zu erstellen.

1. In der **Fehlerliste**, mehrere Warnungen auswählen und dann auf die Warnungen.

2. Zeigen Sie auf **Arbeitsaufgabe erstellen** , und klicken Sie auf den Typ des zu erstellenden Arbeitselements.

     Ein einzelnes Arbeitselement wird für die ausgewählten Warnungen für die Sie angeben, die Fehlerinformationen erstellt.