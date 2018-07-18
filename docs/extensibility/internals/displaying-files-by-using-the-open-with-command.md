---
title: Anzeigen von Dateien Befehl Öffnen mit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9c708bb5a510748b08cac5b46b6829b908e74e0a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128617"
---
# <a name="displaying-files-by-using-the-open-with-command"></a>Anzeigen von Dateien mit Öffnen mit (Befehl)
Ein Projekt kann die IDE anzuzeigenden Fragen der **Öffnen mit** (Dialogfeld). Diese Anforderung fordert den Benutzer zum Öffnen einer Datei, die eine Auswahl von standard-Editoren verfügt. Die folgenden Schritte beschreiben diesen Prozess.  
  
1.  Ruft die Projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, Angabe des Werts OSE_UseOpenWithDialog für die `OSEOpenDocEditor` Parameter.  
  
2.  Basierend auf das Dokument Dateinamenerweiterung, die IDE bestimmt, welche Editoren aufgeführt, die in der Registrierung kann das angegebene Dokument zu öffnen und zeigt diese Informationen in den **Öffnen mit** (Dialogfeld).  
  
    > [!NOTE]
    >  Projekte, die einen systeminternen Editor verfügen, der in enthalten sein müssen die **Öffnen mit** Dialogfeld muss eine Editorfactory für jeden solchen Editor registrieren. Editoren systeminterne Funktion nur zusammen mit der eine bestimmte Art von Projekt, das in der Implementierung der erzwungen wird die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Methode. Die IDE hat eine integrierten Editor-Factory für die Core-Text-Editor und dem Binär-Editor. Die IDE erstellt auch eine Instanz von Editorfactory für jede registrierte Windows-Datei-Zuordnung. Ein Beispiel für eine solche Datei ist Microsoft Word.  
  
3.  Sobald der Benutzer ein Element aus auswählt der **Öffnen mit** (Dialogfeld), klicken Sie dann die IDE Öffnet das Dokument durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode. Weitere Informationen finden Sie unter [Vorgehensweise: Standard-öffnen-Editoren](../../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Anzeigen von Dateien mit dem Befehl Open File](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [Gewusst wie: Öffnen von Standard-Editoren](../../extensibility/how-to-open-standard-editors.md)