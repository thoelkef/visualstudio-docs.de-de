---
title: Anzeigen von Dateien mit dem Befehl "Öffnen mit" | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840914"
---
# <a name="displaying-files-by-using-the-open-with-command"></a>Anzeigen von Dateien mit dem Befehl „Öffnen mit“
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein Projekt kann die IDE bitten, das Dialogfeld **Öffnen mit** anzuzeigen. Diese Anforderung fordert den Benutzer auf, eine Datei zu öffnen, die über eine Auswahl von Standard-Editoren verfügt. Dieser Vorgang wird in den folgenden Schritten beschrieben.  
  
1. Das Projekt ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> auf und gibt den Wert OSE_UseOpenWithDialog für den- `OSEOpenDocEditor` Parameter an.  
  
2. Basierend auf der Dateinamenerweiterung des Dokuments bestimmt die IDE, welche Editoren in der Registrierung das angegebene Dokument öffnen können. diese Informationen werden im Dialogfeld **Öffnen mit** angezeigt.  
  
    > [!NOTE]
    > Projekte mit einem intrinsischen Editor, der in das Dialogfeld **Öffnen mit** eingeschlossen werden muss, müssen für jeden Editor eine Editorfactory registrieren. Intrinsische Editoren funktionieren nur in Verbindung mit einem bestimmten Projekttyp, der in der Implementierung der-Methode erzwungen wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> . Die IDE verfügt über eine integrierte Editorfactory für den Core-Text-Editor und den Binär-Editor. Die IDE erstellt außerdem eine Instanz einer Editorfactory im Namen jeder registrierten Windows-Datei Zuordnung. Ein Beispiel für eine solche Datei ist Microsoft Word.  
  
3. Sobald der Benutzer im Dialogfeld **Öffnen mit** ein Element auswählt, öffnet die IDE das Dokument durch Aufrufen der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode. Weitere Informationen finden Sie unter Gewusst [wie: Öffnen von Standard-Editoren](../../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Öffnen und Speichern von Projekt Elementen](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Anzeigen von Dateien mit dem Befehl "Datei öffnen"](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [Gewusst wie: Öffnen von Standard-Editoren](../../extensibility/how-to-open-standard-editors.md)
