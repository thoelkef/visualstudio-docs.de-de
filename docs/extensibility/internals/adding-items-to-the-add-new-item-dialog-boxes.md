---
title: Hinzufügen von Elementen, die zum Hinzufügen neuer Elemente Dialogfelder | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b98e696def519cea6d3644d0ef3a48bc82c19136
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812581"
---
# <a name="add-items-to-the-add-new-item-dialog-box"></a>Fügen Sie Elemente hinzu, um das Dialogfeld "Neues Element hinzufügen"
Der Prozess zum Hinzufügen von Elementen, die **neues Element hinzufügen** Dialogfeld beginnt mit dem Registrierungsschlüssel. Siehe die folgenden Registrierungseinträge, die **AddItemTemplates** Abschnitt enthält den Pfad und Name des Verzeichnisses in der die Elemente zur Verfügung gestellt der **neues Element hinzufügen** Dialogfeld abgelegt werden.  

> [!NOTE]
>  In der Tabelle, die unmittelbar nach dem Codesegment enthält weitere Informationen zu den Registrierungseintrag an.  

 In diesem Abschnitt befindet sich unter **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects**.

 Die erste GUID ist die CLSID für Projekte dieses Typs. die zweite GUID gibt an, den registrierten Projekttyp für die Vorlagen für Elemente hinzufügen:  

 **\\{C061DB26-5833-11D2-96F5-000000000000} \\AddItemTemplates\\TemplatesDir\\{ACEF4EB2-57CF-11D2-96F4-000000000000}\\1**

 **@** = #6 

 **TemplatesDir** = \\&lt;Visual Studio SDK-Installationspfad&gt;\\VSIntegration\\&lt;SomeFolder&gt; \\ &lt;SomePackage&gt;\\&lt;SomeProject&gt;\\&lt;SomeProjectItems&gt;

 **SortPriority** Dword:00000064 =


| name | Typ | Daten (aus *RGS* Datei) | Beschreibung |
|------------------|-----------| - | - |
| @ (Standard) | REG_SZ | #% IDS_ADDITEM_TEMPLATES_ENTRY % | Ressourcen-ID für **Element hinzufügen** Vorlagen. |
| Val TemplatesDir | REG_SZ | TEMPLATE_PATH %\\&lt;SomeProjectItems&gt; | Pfad der Projektelemente angezeigt, die im Dialogfeld für die **neues Element hinzufügen** Assistenten. |
| Val SortPriority | REG_DWORD | 100 ([!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)]) | Bestimmt die Sortierreihenfolge im Knoten "Struktur" der Dateien angezeigt, der **neues Element hinzufügen** Dialogfeld. |

> [!NOTE]
>  Die GUIDS für die Visual c# und Visual Basic-Projekttypen lauten wie folgt aus: 
> - [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}
> - [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  

 Das Verzeichnis für aufgeführt **TemplatesDir**, d.h. *TEMPLATE_PATH %\\&lt;SomeProjectItems&gt;*, ist der Knoten auf der linken Seite von der **hinzufügen Neues Element** Dialogfeld im Feld-Struktur. Zusätzliche Elemente in der Struktur basieren auf das Unterverzeichnis innerhalb dieses Stammverzeichnis. Die Dateien zum Projekt hinzugefügt werden sind die Elemente im Bereich rechts von der **neues Element hinzufügen** Dialogfeld.  

 Dieser Ordner enthält in der Regel die Vorlagendateien für Ihr Projekt wie z. B. einer HTML-Vorlage oder *cpp* -Datei, und alle *VSZ* Dateien zum Starten des Assistenten. Sie können auch einschließen, um zu steuern, wie die Elemente angezeigt werden, *VSDIR* Dateien zum Lokalisieren von Verzeichnisnamen und Symbole. Die lokalisierte Zeichenfolge wird die Beschriftung im Dialogfeld angezeigt wird, die diesem Knoten in dargestellt die **neues Element hinzufügen** Dialogfeld im Feld-Struktur.  

 Aber Sie müssen nicht alles in einem haben *VSDIR* Datei. Sie haben eine *VSDIR* -Datei für jedes Element in das Verzeichnis. Weitere Informationen finden Sie unter [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md) und [Directory Beschreibung (VSDIR)-Vorlagendateien](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  

> [!NOTE]
>  Die *VSDIR* Dateien in den Verzeichnissen der Vorlage sind optional. Sollten Sie einfach ein Projektelement im Verzeichnis eingefügt, und zeigt es im der **neues Element hinzufügen** im Dialogfeld können Sie diese Datei ablegen, in dem im angegebenen Vorlagenverzeichnis die **TemplatesDir** Anweisung. Die Datei wird dann im rechten Bereich angezeigt werden die **neues Element hinzufügen** im Dialogfeld für das betreffende Projekt. Wenn jedoch eine lokalisierte Beschriftung für die Datei oder ein Symbol angezeigt werden sollen, Sie müssen enthalten mindestens eine *VSDIR* -Datei in das Verzeichnis für Vorlagen.  

## <a name="group-project-items"></a>Gruppe von Projektelementen  
 Wenn Vorlagengruppen in Ordnern im enthalten soll die **neues Element hinzufügen** Dialogfeld-Box-Struktur, benötigen Sie darin enthaltenen Unterverzeichnisse unter dem Stammverzeichnis für die Vorlage mit den Elementen. Wenn die **neues Element hinzufügen** im Dialogfeld für Benutzer angezeigt wird, wird auch die Unterordner und können sie Projektelemente aus.  

 Die Sortierpriorität im Codesegment bestimmt, in dem dieses Vorlagenverzeichnis in der Struktur relativ zu anderen Elementen des Strukturknotens erstellt wird. Für die **neues Element hinzufügen** im Dialogfeld die Sortierpriorität ist alles, was Sie enthalten müssen, damit die Elemente an der aktuellen Position im Dialogfeld angezeigt werden.  

 Sie können auch implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> Schnittstelle zum Filtern der Anzeige auf die **neues Element hinzufügen** Dialogfeld. Durch die Implementierung dieser Schnittstelle können Sie eine Vorlagenverzeichnis einrichten auf dem Datenträger, die enthält, z. B. 50 Dateien von Vorlage und Assistenten. Auf diese Weise haben Sie verschiedene Projekttypen mit 20 Dateien, die zu einem Projekttyp, andere 30 Dateien, die in einen anderen Projekttyp gehören und alle Dateien in einem allgemeinen Typ des Projekts gehören. Auf diese Weise kann je nach welchem Projekt Vorlage erstellt wurde, können Sie einen anderen Satz von Vorlagendateien anzeigen.  

 In einem Visual Basic-Projekt können Sie z. B. Webprojekte und Clientprojekte verfügen. Webformulare sind nicht nützlich, Elemente, die ein Clientprojekt hinzugefügt, und Windows Forms sind nicht nützlich, Elemente, die ein Web-Server-Projekt hinzugefügt. Aus diesem Grund können Sie ein Verzeichnis für Benutzervorlagen erstellen, die alle für beide Typen von Dateien enthält. Klicken Sie dann durch die Implementierung <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>, Sie können Elemente, die nicht angezeigt werden soll, basierend auf dem Typ des Projekts oder der projekteinstellungen im Projekt ausblenden.  

## <a name="filter-project-items"></a>Filtern von Projektelementen  
 `IVsFilterAddProjectItemDlg2` bietet für das Filtern von Elementen in der Struktur (linker Bereich) und die Projektdateien (rechter Bereich) auf folgende Weise:  

- Die lokalisierte Namen (Beschriftungen, die das im Dialogfeld angezeigt, der in enthalten ist die *VSDIR* Datei) gebotenen `IVsFilterAddProjectItemDlg`.  

- Durch die tatsächlichen Namen der Dateien und Ordner auf dem Datenträger (nicht lokalisierten — keine *VSDIR* Datei) gebotenen `IVsFilterAddProjectItemDlg`.  

- Nach der Kategorie von bereitgestellten `IVsFilterAddProjectItemDlg2`.  

  Geben Sie zum Filtern nach Kategorie eine Kategoriezeichenfolge auf ein Element in der *VSDIR* Dateien wie *Webformular* oder *Clientelement* in Visual Basic. Der DialogfeldCode ruft dann die Kategorie-Klassifizierung aus der *VSDIR* Datei und übergibt sie an Sie. Sie können diese Informationen dann übergeben, für Ihre Implementierung der `IVsFilterAddProjectItemDlg2` zum Filtern der **neues Element hinzufügen** Dialogfeld nach Kategorien. Sie können auch Elemente für Webseiten oder als Client Win32-Anwendungsfällen filtern. Darüber hinaus können Sie identifizieren [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] mit Elementen Microsoft Foundation Classes (MFC) oder active-Vorlagenelementen Library (ATL) bezeichnet. Wenn Sie diese Elemente identifizieren, kann das Projektsystem einen eigenen Klassifizierungen definieren, sodass das System basierend auf Kategorien und Klassifizierungen gefiltert werden kann.  

  Wenn Sie diese Filter-Funktion implementieren, müssen Sie keine Tabelle mit jedem Element zugeordnet werden, die ausgeblendet werden soll. Sie können einfach klassifiziert Elemente in Typen, und fügen Sie die Klassifizierungen in der *VSDIR* Dateien. Anschließend können Sie eines der Elemente ausblenden, die eine bestimmte Klassifizierung durch Implementieren der Schnittstelle. Auf diese Weise können Sie vornehmen, die Elemente in der **neues Element hinzufügen** Dialogfeld Feld dynamisch basierend auf den Zustand innerhalb des Projekts.  

## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)   
 [CATIDs für Objekte, die in der Regel zum Erweitern von Projekten verwendet werden](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Vorlagendateien für Verzeichnis-Beschreibung (VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)