---
title: Toolboxelemente auswählen, WPF-Komponenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
ms.assetid: 6ce1d178-88c0-4295-8915-59fdeedabb11
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 057f354b06002c9b1708478f3e3a9592a47a7065
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515200"
---
# <a name="choose-toolbox-items-wpf-components"></a>Toolboxelemente auswählen, WPF-Komponenten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Toolboxelemente auswählen, WPF-Komponenten](https://docs.microsoft.com/visualstudio/ide/reference/choose-toolbox-items-wpf-components).  
  
  
Auf dieser Registerkarte des Dialogfelds **Toolboxelemente auswählen** wird eine Liste der Windows Presentation Foundation (WPF)-Steuerelemente angezeigt, die auf dem lokalen Computer verfügbar sind. Um diese Liste anzuzeigen, wählen Sie im Menü **Extras** die Option **Toolboxelemente auswählen** aus, um das Dialogfeld **Toolboxelemente auswählen** aufzurufen. Wählen Sie anschließend die Registerkarte **WPF-Komponenten** aus. Klicken Sie zum Sortieren der aufgeführten Komponenten auf eine beliebige Spaltenüberschrift.  
  
-   Wenn das Kontrollkästchen neben einer Komponente aktiviert wird, wird für diese Komponente in der **Toolbox** ein Symbol aufgeführt.  
  
    > [!TIP]
    >  Um zu einem projektspezifischen Dokument, das zur Bearbeitung geöffnet ist, eine Instanz eines WPF-Steuerelements hinzuzufügen, ziehen Sie dessen Symbol **Toolbox** auf die Entwurfsoberfläche. Standardmarkup und Code für die Komponente werden in das Projekt eingefügt und können bearbeitet werden. Weitere Informationen finden Sie unter [How to: Manage the Toolbox Window (Vorgehensweise: Verwalten des Toolbox-Fensters)](http://msdn.microsoft.com/en-us/a022c3fe-298c-4a59-a48f-b050da90ebc2) und [Vorgehensweise: Ändern von Registerkarten der Toolbox](http://msdn.microsoft.com/en-us/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
-   Wenn das Kontrollkästchen neben einer Komponente deaktiviert wird, wird das zugehörige Symbol aus der **Toolbox** entfernt.  
  
    > [!NOTE]
    >  Die auf dem Computer installierten .NET Framework-Komponenten bleiben verfügbar, und zwar unabhängig davon, ob für sie Symbole in der **Toolbox** angezeigt werden.  
  
 Die Spalten auf der Registerkarte **WPF-Komponenten** enthalten die folgenden Informationen:  
  
 name  
 Listet die Namen der WPF-Steuerelemente auf, für die Einträge in der Registrierung des Computers vorhanden sind.  
  
 Namespace  
 Zeigt die Hierarchie des [NIB: .NET Framework-Klassenbibliothek](http://msdn.microsoft.com/en-us/6c4f3a62-6a0f-41f2-9d52-ee0b13686f29)-Namespaces an, der die Struktur der Komponente definiert. Wenn Sie nach dieser Spalte sortieren, werden die verfügbaren Komponenten innerhalb der einzelnen auf dem Computer installierten .NET Framework-Namespaces aufgeführt.  
  
 Assemblyname  
 Zeigt den Namen der .NET Framework-Assembly an, die den Namespace der einzelnen Komponenten enthält. Wenn Sie nach dieser Spalte sortieren, werden die Namespaces innerhalb der einzelnen auf dem Computer installierten .NET Framework-Assemblys aufgeführt.  
  
 Verzeichnis  
 Zeigt den Speicherort der .NET Framework-Assembly an. Der Standardspeicherort für alle Assemblys ist der globale Assemblycache. Weitere Informationen über den globalen Assemblycache finden Sie unter [Arbeiten mit Assemblys und dem globalen Assemblycache](http://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433).  
  
## <a name="uielement-list"></a>UIElement-Liste  
 **Filter**  
 Filtert die Liste der WPF-Steuerelemente auf Grundlage der Zeichenfolge, die Sie im Textfeld bereitstellen. Alle Übereinstimmungen aus den vier Spalten werden angezeigt.  
  
 **Clear** (Löschen)  
 Löscht die Filterzeichenfolge.  
  
 **Browse** (Durchsuchen)  
 Öffnet das Dialogfeld **Öffnen**, mit dem Sie zu Assemblys navigieren können, die WPF-Steuerelemente enthalten. Hier können Sie Assemblys laden, die sich nicht im globalen Assemblycache befinden.  
  
 **Sprache**  
 Zeigt die lokalisierte Sprache der Assembly an, die das ausgewählte WPF-Steuerelement enthält.  
  
## <a name="limitations"></a>Einschränkungen  
 Beim Hinzufügen eines benutzerdefinierten Steuerelements oder <xref:System.Windows.Controls.UserControl> zur Toolbox gibt es folgende Einschränkungen.  
  
-   Es funktioniert nur bei benutzerdefinierten Steuerelementen, die außerhalb des aktuellen Projekts definiert sind.  
  
-   Es wird nicht ordnungsgemäß aktualisiert, wenn die Konfiguration der Projektmappe vom Debugmodus in den Releasemodus oder vom Releasemodus in den Debugmodus geändert wird. Der Grund hierfür ist, dass der Verweis nicht auf ein Projekt, sondern auf die Assembly auf der Festplatte verweist. Wenn das Steuerelement Teil der aktuellen Projektmappe ist und vom Debugmodus in den Releasemodus gewechselt wird, verweist das Projekt weiterhin auf die Debugversion des Steuerelements.  
  
 Wenn Entwurfszeit-Metadaten auf das benutzerdefinierte Steuerelement angewendet werden und diese Metadaten angeben, dass <xref:Microsoft.Windows.Design.ToolboxBrowsableAttribute> auf `false` festgelegt ist, wird das Steuerelement nicht in der Toolbox angezeigt.  
  
 Sie können direkt in der XAML-Ansicht auf die Steuerelemente verweisen, indem Sie den Namespace und die Assembly für das Steuerelement zuordnen. Weitere Informationen finden Sie unter [Vorgehensweise: Importieren eines Namespace in XAML](http://msdn.microsoft.com/en-us/6cda7c7a-369c-47dd-9c2d-13a35dcf737c).  
  
## <a name="see-also"></a>Siehe auch  
 [Dialogfeld „Toolboxelemente auswählen“ (Visual Studio)](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb)   
 [Toolbox](../../ide/reference/toolbox.md)   
 [Vorgehensweise: Verwenden eines WPF-Steuerelements eines Drittanbieters in der WPF-Anwendung](http://msdn.microsoft.com/en-us/f4c0b601-3818-4f9f-85e5-77905f3b427f)   
 [WPF-Designer](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)



