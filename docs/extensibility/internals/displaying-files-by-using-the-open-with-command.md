---
title: "Anzeigen von Dateien Befehl Öffnen mit | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ed8a19ce0cfb6a7936d61ff7a5855498d2010359
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
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