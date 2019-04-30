---
title: Anzeigen von Dateien öffnen mit-Befehl mit | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: de43b6c4f441f8c6bde2d6c248274aed3937a7ee
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63408812"
---
# <a name="displaying-files-by-using-the-open-with-command"></a>Anzeigen von Dateien mit dem Befehl „Öffnen mit“
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein Projekt lassen die IDE zum Anzeigen der **Öffnen mit** Dialogfeld. Diese Anforderung fordert den Benutzer zum Öffnen einer Datei, die eine Auswahl von standard-Editoren. Die folgenden Schritte beschreiben, diesen Prozess.  
  
1. Die projektaufrufe <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, geben Sie einen Wert OSE_UseOpenWithDialog für die `OSEOpenDocEditor` Parameter.  
  
2. Basierend auf der Dateinamenerweiterung des Dokuments ab, die IDE bestimmt, welche Editoren aufgeführt, die in der Registrierung kann das angegebene Dokument geöffnet und zeigt diese Informationen in den **Öffnen mit** Dialogfeld.  
  
    > [!NOTE]
    > Projekte, die einen systeminternen Editor verfügen, die im enthalten sein müssen die **Öffnen mit** im Dialogfeld eine Editorfactory für jeden solchen Editor registrieren muss. Systeminterne Editoren funktionieren nur zusammen mit der eine bestimmte Art von Projekt, das in der Implementierung der erzwungen wird die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Methode. Die IDE hat eine integrierten Editorfactory für die kerntext-Editor und dem Binär-Editor. Die IDE erstellt auch eine Instanz von einer Editorfactory für jede registrierte Windows-dateizuordnung. Ein Beispiel für eine solche Datei ist Microsoft Word.  
  
3. Sobald der Benutzer ein Element auswählt der **Öffnen mit** (Dialogfeld), klicken Sie dann die IDE Öffnet das Dokument durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen Sie die Standard-Editoren](../../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Sie öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Anzeigen von Dateien mit dem Befehl Open File](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [Vorgehensweise: Öffnen von Standard-Editoren](../../extensibility/how-to-open-standard-editors.md)
