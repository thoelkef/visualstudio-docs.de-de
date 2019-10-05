---
title: Toolboxelemente auswählen, WPF-Komponenten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
ms.assetid: 6ce1d178-88c0-4295-8915-59fdeedabb11
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3f17ac56038c5f6c1d4de026546410ece438e375
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68869931"
---
# <a name="choose-toolbox-items-wpf-components"></a>Toolboxelemente auswählen, WPF-Komponenten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Auf dieser Registerkarte des Dialogfelds **Toolboxelemente auswählen** wird eine Liste der Windows Presentation Foundation (WPF)-Steuerelemente angezeigt, die auf dem lokalen Computer verfügbar sind. Um diese Liste anzuzeigen, wählen Sie im Menü **Extras** die Option **Toolboxelemente auswählen** aus, um das Dialogfeld **Toolboxelemente auswählen** aufzurufen. Wählen Sie anschließend die Registerkarte **WPF-Komponenten** aus. Klicken Sie zum Sortieren der aufgeführten Komponenten auf eine beliebige Spaltenüberschrift.

- Wenn das Kontrollkästchen neben einer Komponente aktiviert wird, wird für diese Komponente in der **Toolbox** ein Symbol aufgeführt.

  > [!TIP]
  > Um zu einem projektspezifischen Dokument, das zur Bearbeitung geöffnet ist, eine Instanz eines WPF-Steuerelements hinzuzufügen, ziehen Sie dessen Symbol **Toolbox** auf die Entwurfsoberfläche. Standardmarkup und Code für die Komponente werden in das Projekt eingefügt und können bearbeitet werden. Weitere Informationen finden Sie unter [How to: Manage the Toolbox Window (Vorgehensweise: Verwalten des Toolbox-Fensters)](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2) und [Vorgehensweise: Ändern von Registerkarten der Toolbox](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).

- Wenn das Kontrollkästchen neben einer Komponente deaktiviert wird, wird das zugehörige Symbol aus der **Toolbox** entfernt.

  > [!NOTE]
  > Die auf dem Computer installierten .NET Framework-Komponenten bleiben verfügbar, und zwar unabhängig davon, ob für sie Symbole in der **Toolbox** angezeigt werden.

  Die Spalten auf der Registerkarte **WPF-Komponenten** enthalten die folgenden Informationen:

  Name listet die Namen der WPF-Steuerelemente auf, für die Einträge in der Registrierung Ihres Computers vorhanden sind.

  Namespace zeigt die Hierarchie des [NIB an: .NET Framework Klassenbibliothek](https://msdn.microsoft.com/6c4f3a62-6a0f-41f2-9d52-ee0b13686f29) -Namespace, der die Struktur der Komponente definiert. Wenn Sie nach dieser Spalte sortieren, werden die verfügbaren Komponenten innerhalb der einzelnen auf dem Computer installierten .NET Framework-Namespaces aufgeführt.

  AssemblyName zeigt den Namen der .NET Framework Assembly an, die den Namespace für jede Komponente enthält. Wenn Sie nach dieser Spalte sortieren, werden die Namespaces innerhalb der einzelnen auf dem Computer installierten .NET Framework-Assemblys aufgeführt.

  Verzeichnis zeigt den Speicherort der .NET Framework Assembly an. Der Standardspeicherort für alle Assemblys ist der globale Assemblycache. Weitere Informationen über den globalen Assemblycache finden Sie unter [Arbeiten mit Assemblys und dem globalen Assemblycache](https://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433).

## <a name="uielement-list"></a>UIElement-Liste
 **Filter** Filtert die Liste der WPF-Steuerelemente auf Grundlage der Zeichenfolge, die Sie im Textfeld angeben. Alle Übereinstimmungen aus den vier Spalten werden angezeigt.

 **Löschen** Löscht die Filter Zeichenfolge.

 **Durchsuchen** Öffnet das Dialogfeld **Öffnen** , in dem Sie zu Assemblys navigieren können, die WPF-Steuerelemente enthalten. Hier können Sie Assemblys laden, die sich nicht im globalen Assemblycache befinden.

 **Sprache** Zeigt die lokalisierte Sprache der Assembly an, die das ausgewählte WPF-Steuerelement enthält.

## <a name="limitations"></a>Einschränkungen
 Beim Hinzufügen eines benutzerdefinierten Steuerelements oder <xref:System.Windows.Controls.UserControl> zur Toolbox gibt es folgende Einschränkungen.

- Es funktioniert nur bei benutzerdefinierten Steuerelementen, die außerhalb des aktuellen Projekts definiert sind.

- Es wird nicht ordnungsgemäß aktualisiert, wenn die Konfiguration der Projektmappe vom Debugmodus in den Releasemodus oder vom Releasemodus in den Debugmodus geändert wird. Der Grund hierfür ist, dass der Verweis nicht auf ein Projekt, sondern auf die Assembly auf der Festplatte verweist. Wenn das Steuerelement Teil der aktuellen Projektmappe ist und vom Debugmodus in den Releasemodus gewechselt wird, verweist das Projekt weiterhin auf die Debugversion des Steuerelements.

  Wenn außerdem Entwurfszeit Metadaten auf das benutzerdefinierte Steuerelement angewendet werden und diese Metadaten angeben, dass das [ToolboxBrowsableAttribute](/previous-versions/visualstudio/visual-studio-2010/bb547991(v=vs.100)) auf `false`festgelegt ist, wird das Steuerelement nicht in der Toolbox angezeigt.

  Sie können direkt in der XAML-Ansicht auf die Steuerelemente verweisen, indem Sie den Namespace und die Assembly für das Steuerelement zuordnen. Weitere Informationen finden Sie unter [Vorgehensweise: Importieren eines Namespace in XAML](https://msdn.microsoft.com/6cda7c7a-369c-47dd-9c2d-13a35dcf737c).

## <a name="see-also"></a>Siehe auch

- [Dialogfeld „Toolboxelemente auswählen“ (Visual Studio)](https://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)
- [Werkzeugkasten](../../ide/reference/toolbox.md)
- [Vorgehensweise: Verwenden eines WPF-Steuerelements eines Drittanbieters in der WPF-Anwendung](https://msdn.microsoft.com/f4c0b601-3818-4f9f-85e5-77905f3b427f)
- [WPF-Designer](https://msdn.microsoft.com/c6c65214-8411-4e16-b254-163ed4099c26)