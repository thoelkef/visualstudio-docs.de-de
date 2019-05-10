---
title: 'Vorgehensweise: Erstellen eines Arbeitselements für einen Fehler in verwaltetem Code'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed code, creating work items for code defects
- code analysis, creating work items
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e2e55ddf51e0c81f57c504e398c23c8e1d3f721a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816667"
---
# <a name="how-to-create-a-work-item-for-a-managed-code-defect"></a>Vorgehensweise: Erstellen eines Arbeitselements für einen Fehler in verwaltetem Code

Sie können die Arbeit Element-Überwachungsfunktion mit Protokolldatei für eine Arbeitsaufgabe aus in Visual Studio verwenden. Um dieses Feature verwenden zu können, muss Ihr Projekt Teil eines Azure DevOps-Projekts in [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)].

## <a name="to-create-a-work-item-for-managed-code-defect"></a>Um ein Arbeitselement für Fehler in verwaltetem Code zu erstellen.

1. In der **Codeanalyse** Fenster, wählen Sie die Warnung.

2. Wählen Sie **Aktionen**, wählen Sie dann **Arbeitsaufgabe erstellen** , und wählen Sie den Typ des zu erstellenden Arbeitselements.

     Ein neues Arbeitselement erstellt für Sie um die Fehler anzugeben.

## <a name="to-create-a-work-item-for-multiple-managed-code-defects"></a>Um ein Arbeitselement für mehrere Fehlern in verwaltetem Code zu erstellen.

1. In der **Fehlerliste**, mehrere Warnungen auswählen und dann auf die Warnungen.

2. Zeigen Sie auf **Arbeitsaufgabe erstellen** , und klicken Sie auf den Typ des zu erstellenden Arbeitselements.

     Ein einzelnes Arbeitselement wird für die ausgewählten Warnungen für die Sie angeben, die Fehlerinformationen erstellt.