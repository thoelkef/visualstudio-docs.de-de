---
title: Die Arbeitsmappe enthält ActiveX-Steuerelemente, die nicht geladen werden können.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: error-reference
f1_keywords:
- VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 09182fb354ad3ae8937b66952a0acd376d54fe0a
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584450"
---
# <a name="the-workbook-contains-activex-controls-that-cannot-be-loaded"></a>Die Arbeitsmappe enthält ActiveX-Steuerelemente, die nicht geladen werden können.

  Der Fehler "die zum Erstellen dieses Projekts verwendete Arbeitsmappe enthält ActiveX-Steuerelemente, die vom Designer nicht geladen werden können" wird angezeigt, wenn Sie ein Steuerelement einem Word-Dokument oder einem Excel-Arbeitsblatt Programm gesteuert hinzufügen, das Dokument oder die Arbeitsmappe speichern und dann eine neue Lösung auf Dokument Ebene basierend auf dem Dokument oder der Arbeitsmappe erstellen.

 Informationen über den verwalteten Typ des Steuerelements wird nicht zusammen mit dem Dokument oder der Arbeitsmappe gespeichert. Wenn Sie eine neue Lösung basierend auf diesem Dokument oder dieser Arbeitsmappe erstellen, hat Visual Studio nicht genügend Informationen, um das Steuerelement im Hostelement-Designer zu laden.

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Öffnen Sie das Dokument oder die Arbeitsmappe.

2. Entfernen Sie die Steuerelemente, die zur Laufzeit hinzugefügt wurden. Hierzu können Sie diese im Dokument oder **in der Arbeits** Mappe auswählen und die ENTF-Taste drücken.

3. Erstellen Sie eine Lösung auf Dokumentebene basierend auf dem Dokument oder der Arbeitsmappe.

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)
