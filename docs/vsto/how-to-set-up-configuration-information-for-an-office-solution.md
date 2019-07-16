---
title: Einrichten von Konfigurationsinformationen für eine Office-Projektmappe
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c477068b3aee3325acae0887e11da908d6c33a85
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328897"
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>Vorgehensweise: Einrichten von Konfigurationsinformationen für eine Office-Projektmappe
  Sie können Konfigurationsdateien verwenden, um Einstellungen zu konfigurieren, die spezifisch für Ihre Office-Projektmappen sind. Sie können Einstellungen wie z. B. assemblybindungsrichtlinien, Remotingobjekte, Debug und Trace-Einstellungen angeben.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-configuration-file-to-your-office-project"></a>Um eine Konfigurationsdatei auf dem Office-Projekt hinzufügen

1. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

2. In der **Kategorien** Bereich, klicken Sie auf **allgemeine**.

3. In der **Vorlagen** wählen Sie im Bereich **Anwendungskonfigurationsdatei**.

4. In der **Namen** geben den gleichen Namen der Assembly mit der Erweiterung *config*. Beispielsweise eine Konfigurationsdatei für eine Assembly der Excel-Projekt namens *ExcelWorkbook1.dll* hieße *ExcelWorkbook1.dll.config*.

5. Klicken Sie auf **Hinzufügen**.

6. Erstellen Sie die Konfigurationsdatei entsprechend der Anwendung Konfigurationsdateischema. Weitere Informationen finden Sie unter [Konfigurationsdateischema für .NET Framework](/dotnet/framework/configure-apps/file-schema/index).

   Es gibt keine besonderen Überlegungen für die Verwendung von Konfigurationsdateien mit Office-Projekten.

## <a name="see-also"></a>Siehe auch
- [Konfigurationsdateischema für .NET Framework](/dotnet/framework/configure-apps/file-schema/index)
- [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)
- [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)
