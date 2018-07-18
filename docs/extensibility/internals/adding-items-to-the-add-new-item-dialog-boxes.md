---
title: Hinzufügen von Elementen, die zum Hinzufügen neuer Elemente Dialogfelder | Microsoft Docs
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
ms.openlocfilehash: a24a6d531812a170768f8c100f14ad64ab1e68c5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135065"
---
# <a name="adding-items-to-the-add-new-item-dialog-boxes"></a>Hinzufügen von Elementen, die zum Hinzufügen neuer Elemente Dialogfelder
Der Prozess zum Hinzufügen von Elementen der **neues Element hinzufügen** Dialogfeld beginnt mit dem Registrierungsschlüssel. Wie in der folgenden Registrierungseinträge gezeigt, wird der Abschnitt AddItemTemplates enthält, den Pfad und den Namen des Verzeichnisses in der Elemente im zur Verfügung gestellt der **neues Element hinzufügen** Dialogfeld abgelegt werden.  
  
> [!NOTE]
>  Die Tabelle, die unmittelbar nach dem Codesegment enthält zusätzliche Informationen zu den Registrierungseintrag an.  
  
 In diesem Abschnitt finden Sie unter [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects].  
  
 Die erste GUID ist die CLSID für Projekte dieses Typs. die zweite GUID gibt an, die registrierten Projekttyp für die Vorlagen für Elemente hinzufügen.  
  
 \\{C061DB26-5833-11D2-96F5-000000000000} \AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000} \1  
  
 @="#6"  
  
 "TemplatesDir"="\<Visual Studio SDK-Installationspfad\\\VSIntegration\\\SomeFolder\\\SomePackage\\\SomeProject\\\SomeProjectItems"  
  
 "SortPriority" = Dword:00000064  
  
|name|Typ|Daten (aus RGS-Datei)|Beschreibung|  
|----------|----------|-----------------------------|-----------------|  
|@ (Standard)|REG_SZ|#% IDS_ADDITEM_TEMPLATES_ENTRY %|Ressourcen-ID für **Element hinzufügen** Vorlagen.|  
|Val-TemplatesDir|REG_SZ|%TEMPLATE_PATH%\ SomeProjectItems|Pfad der Projektelemente angezeigt, die im Dialogfeld für die **neues Element hinzufügen** Assistenten.|  
|Val-SortPriority|REG_DWORD|100 ([!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)])|Bestimmt die Sortierreihenfolge in der Strukturknoten der Dateien angezeigt, der **neues Element hinzufügen** (Dialogfeld).|  
  
> [!NOTE]
>  Die GUIDS für die Visual c# und Visual Basic-Projekttypen lauten wie folgt:[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  
  
 Das Verzeichnis aufgelistet, für TemplateDirs, d. h. % TEMPLATE_PATH%\SomeProjectItems, der Knoten auf der linken Seite des ist die **neues Element hinzufügen** Dialogfeld Feld Struktur. Zusätzliche Elemente in der Struktur basieren auf das Unterverzeichnis innerhalb dieses Stammverzeichnisses befinden. Die Dateien zum Projekt hinzugefügt werden, sind die Elemente im rechten Bereich von der **neues Element hinzufügen** (Dialogfeld).  
  
 Dieser Ordner wird in der Regel die Vorlagendateien für das Projekt z. B. eine Vorlage HTML oder cpp-Datei und alle VSZ-Dateien zum Starten des Assistenten enthalten. Um zu steuern, wie die Elemente angezeigt werden, können Sie auch VSDIR-Dateien zum Lokalisieren von Verzeichnisnamen und Symbole einschließen. Die lokalisierte Zeichenfolge ist die Beschriftung, die Sie im Dialogfeld angezeigt wird, die diesem Knoten in der Struktur der neues Element hinzufügen-Dialogfeld darstellt.  
  
 Allerdings müssen Sie nicht alles in einer VSDIR-Datei haben. Sie können eine VSDIR-Datei für jedes Element im Verzeichnis haben. Weitere Informationen finden Sie unter [Assistenten (. VSZ) Datei](../../extensibility/internals/wizard-dot-vsz-file.md) und [Vorlagenbeschreibung-Verzeichnis (. VSDIR)-Dateien](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
> [!NOTE]
>  Der VSDIR-Dateien in den Verzeichnissen der Vorlage sind optional. Wenn Sie einfach nur einem Project-Element in das Verzeichnis abgelegt werden, und zeigen Sie sie in der **neues Element hinzufügen** (Dialogfeld), können Sie dieser Datei legen Sie im Vorlagenverzeichnis in der TemplatesDir-Anweisung angegeben. Die Datei wird dann im rechten Bereich angezeigt werden die **neues Element hinzufügen** Dialogfeld für das betreffende Projekt. Wenn Sie eine lokalisierte Beschriftung für die Datei oder ein Symbol anzeigen möchten, müssen Sie mindestens eine VSDIR-Datei im Vorlagenverzeichnis einschließen.  
  
## <a name="grouping-project-items"></a>Gruppierung-Projektelemente  
 Wenn Vorlagengruppen in Ordnern enthalten soll die **neues Element hinzufügen** Dialogfeld Feld Struktur, benötigen Sie diese Unterverzeichnisse unter dem Stammverzeichnis für die Vorlage mit den Elementen. Wenn die **neues Element hinzufügen** im Dialogfeld für Benutzer angezeigt wird, wird außerdem finden Sie in den Unterordnern und Projektelementen daraus auswählen können.  
  
 Die Sortierpriorität im Codesegment bestimmt, wo dieses Verzeichnisses für die Vorlage in der Struktur relativ zu anderen Elementen des Strukturknotens erstellt wird. Für die **neues Element hinzufügen** (Dialogfeld), die Sortierpriorität ist alles, die Sie einschließen muss, damit die Elemente in den richtigen Speicherort im Dialogfeld angezeigt werden.  
  
 Sie können auch implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> Schnittstelle zum Filtern der Anzeige auf die **neues Element hinzufügen** (Dialogfeld). Durch die Implementierung dieser Schnittstelle können können Sie richten Sie eine Vorlagenverzeichnis auf dem Datenträger, die enthält, z. B. 50 Vorlage und Assistenten-Dateien. Auf diese Weise haben Sie verschiedene Projekttypen mit 20 Dateien, die auf einen Projekttyp und die 30 Dateien, die zu einem anderen Projekttyp gehören alle Dateien in einem allgemeinen Typ von Projekt gehören. Auf diese Weise je nach dem Projektmanager Vorlage erstellt wurde, können Sie einen anderen Satz von Vorlagendateien anzeigen.  
  
 In einem Visual Basic-Projekt können Sie z. B. Webprojekte und clientprojekten verfügen. WebForms sind nicht nützliche Elemente ein Clientprojekt hinzu, und Windows Forms nicht nützlich Elemente, die eine Web-Server-Projekt hinzugefügt. Aus diesem Grund können Sie ein Verzeichnis erstellen, die alle Dateien für beide Typen des Projekts enthält. Klicken Sie dann durch die Implementierung <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>, Sie können Elemente, die nicht angezeigt werden soll, basierend auf dem Typ des Projekts oder im Projekt projekteinstellungen ausblenden.  
  
## <a name="filtering-project-items"></a>Filtern von Projektelementen  
 `IVsFilterAddProjectItemDlg2` Stellt für das Filtern von Elementen in der Struktur (links) und die Projektdateien (rechter Bereich) auf folgende Weise:  
  
-   Nach den lokalisierten Namen (Beschriftungen, die in der VSDIR-Datei enthalten sind im Dialogfeld angezeigt) gebotenen `IVsFilterAddProjectItemDlg`.  
  
-   Durch die tatsächlichen Namen der Dateien und Ordner auf dem Datenträger (nicht lokalisierten – keine VSDIR-Datei) von bereitgestellten `IVsFilterAddProjectItemDlg`.  
  
-   Nach der Kategorie gebotenen `IVsFilterAddProjectItemDlg2`.  
  
 Geben Sie eine Kategoriezeichenfolge auf ein Element in der VSDIR-Datei, z. B. "Web Form" oder "Client-Item" in Visual Basic, zum Filtern nach Kategorie. Der DialogfeldCode dann Ruft die Kategorie-Klassifizierung aus der VSDIR-Datei ab und übergibt sie an Sie. Sie können dann diese Informationen auf Ihre Implementierung übergeben `IVsFilterAddProjectItemDlg2` zum Filtern der **neues Element hinzufügen** Dialogfeld nach Kategorien. Sie können Elemente auch filtern, für die Webseiten oder Client Win32-Anwendungsfällen. Darüber hinaus können Sie identifizieren [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Elemente wie Microsoft Foundation Classes (MFC) oder active-Vorlagenelementen Library (ATL) gekennzeichnet. Wenn Sie diese Elemente identifizieren, kann das Projektsystem eigene Klassifizierungen definieren, sodass im System basierend auf Kategorien und Klassifizierungen gefiltert werden kann.  
  
 Wenn Sie diese Filter-Funktion implementieren, müssen Sie keine Tabelle mit jedem Element zugeordnet werden, die ausgeblendet werden soll. Sie können einfach klassifizieren Elemente in Typen und versetzen die Klassifizierungen in der VSDIR-Datei oder Dateien. Dann können Sie eines der Elemente ausblenden, die eine bestimmte Klassifizierung durch Implementieren der Schnittstelle haben. Auf diese Weise können Sie machen die Elemente in der **neues Element hinzufügen** Dialogfeld Feld dynamisch basierend auf den Status innerhalb des Projekts.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)   
 [CATIDs für Objekte, die in der Regel verwendet werden, um Projekte zu erweitern.](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Beschreibung der Vorlage Verzeichnis (. VSDIR)-Dateien](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)