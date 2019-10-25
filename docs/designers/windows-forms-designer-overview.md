---
title: Entwerfen von Windows Forms-Anwendungen
ms.date: 08/09/2019
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms Designer
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b26ad18da19d5a2e53199b49e7acc024c728be9c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72634026"
---
# <a name="windows-forms-designer-overview"></a>Übersicht über Windows Forms-Designer

Windows Forms-Designer in Visual Studio bietet eine schnelle Entwicklungslösung zum Erstellen Windows Forms-basierten Anwendungen. Mit Windows Forms-Designer können Sie einem Formular einfach Steuerelemente hinzuzufügen, diese anordnen und Code für deren Ereignisse zu schreiben. Weitere Informationen zu Windows Forms finden Sie auf der Seite mit der [Übersicht über Windows Forms](/dotnet/framework/winforms/windows-forms-overview).

## <a name="functionality"></a>Funktionalität

Mit dem-Designer können Sie folgende Aktionen ausführen:

- Hinzufügen von Komponenten, Datensteuerelementen oder Windows-basierten Steuerelementen zu einem Formular.

- Doppelklicken Sie auf das Formular im Designer und schreiben Sie Code in das Ereignis `Load` für dieses Formular, oder doppelklicken Sie auf ein Steuerelement auf dem Formular und schreiben Sie Code für das Standardereignis des Steuerelements.

- Bearbeiten Sie die Text-Eigenschaft eines Steuerelements, indem Sie das Steuerelement auswählen und einen Namen eingeben.

- Passen Sie die Platzierung des ausgewählten Steuerelements an, indem Sie es mit der Maus oder den Pfeiltasten verschieben. Mit STRG und den Pfeiltasten können Sie das Steuerelement genauer platzieren. Passen Sie abschließend über die die UMSCHALTTASTE und die Pfeiltasten die Größe des Steuerelements an.

- Wählen Sie mehrere Steuerelemente aus, indem Sie entweder **UMSCHALT** oder **STRG** auswählen, während Sie klicken. Wenn Sie **UMSCHALT** + Klick verwenden, ist das erste ausgewählte Steuerelement das bestimmende Steuerelement beim Ausrichten oder Bearbeiten der Größe. Bei Verwendung von**STRG** + Klick ist das zuletzt ausgewählte Steuerelement das bestimmende, sodass sich das bestimmende Steuerelement mit jedem neu hinzugefügten Steuerelement ändert. Alternativ können Sie mehrere Steuerelemente auswählen, indem Sie ein Auswahlrechteck um die Steuerelemente ziehen, die Sie auswählen möchten.

> [!NOTE]
> Verwenden Sie Windows Forms-Designer und nicht den Ressourcen-Editor, um Änderungen an der Ressourcendatei ( *. resx*) eines Formulars vorzunehmen. Wenn Sie eine formularbasierte RESX-Datei bearbeiten, wird eine Warnung angezeigt, dass Änderungen, die Sie im Ressourcen-Editor vornehmen, verloren gehen können. Dies liegt daran, dass der Windows Forms-Designer die RESX-Datei generiert.

## <a name="see-also"></a>Siehe auch

- [Übersicht über Windows Forms](/dotnet/framework/winforms/windows-forms-overview)
- [Windows Forms-Steuerelemente](/dotnet/framework/winforms/controls/)
- [Benutzereingaben in Windows Forms](/dotnet/framework/winforms/user-input-in-windows-forms)
- [Datenbindung in Windows Forms](/dotnet/framework/winforms/windows-forms-data-binding)
- [Verbessern von Windows Forms-Apps](/dotnet/framework/winforms/advanced/)
- <xref:System.Windows.Forms?displayProperty=fullName>API-Referenz