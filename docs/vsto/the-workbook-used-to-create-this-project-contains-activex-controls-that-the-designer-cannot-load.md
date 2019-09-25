---
title: Die zum Erstellen des Projekts verwendete Arbeitsmappe enthält ActiveX-Steuerelemente, die vom Designer nicht geladen werden können.
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 27feb1c6a85740d8a9287ce3a2a47800595e178a
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253777"
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>Die zum Erstellen des Projekts verwendete Arbeitsmappe enthält ActiveX-Steuerelemente, die vom Designer nicht geladen werden können.
  Dieser Fehler wird angezeigt, wenn Sie ein Steuerelement einem Word-Dokument oder einem Excel-Arbeitsblatt programmgesteuert hinzufügen, das Dokument oder die Arbeitsmappe speichern, und dann eine neue Lösung auf Dokumentebene basierend auf dem Dokument oder der Arbeitsmappe erstellen.

 Informationen über den verwalteten Typ des Steuerelements wird nicht zusammen mit dem Dokument oder der Arbeitsmappe gespeichert. Wenn Sie eine neue Lösung basierend auf diesem Dokument oder dieser Arbeitsmappe erstellen, hat Visual Studio nicht genügend Informationen, um das Steuerelement im Hostelement-Designer zu laden.

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Öffnen Sie das Dokument oder die Arbeitsmappe.

2. Entfernen Sie die Steuerelemente, die zur Laufzeit hinzugefügt wurden. Hierzu können Sie diese im Dokument oder **in der Arbeits** Mappe auswählen und die ENTF-Taste drücken.

3. Erstellen Sie eine Lösung auf Dokumentebene basierend auf dem Dokument oder der Arbeitsmappe.

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)
