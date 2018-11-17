---
title: Hinzufügen von Elementen, die zum Hinzufügen neuer Elemente Dialogfelder | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ca9ae7d9e4f0ffc031d2dc8db3e940c9b844c57e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778552"
---
# <a name="adding-items-to-the-add-new-item-dialog-boxes"></a>Hinzufügen von Elementen zu den Dialogfeldern „Neues Element hinzufügen“
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Der Prozess zum Hinzufügen von Elementen, die **neues Element hinzufügen** Dialogfeld beginnt mit dem Registrierungsschlüssel. Siehe die folgenden Registrierungseinträge, Abschnitt AddItemTemplates enthält den Pfad und den Namen des Verzeichnisses in der die Elemente zur Verfügung gestellt der **neues Element hinzufügen** Dialogfeld abgelegt werden.  
  
> [!NOTE]
>  In der Tabelle, die unmittelbar nach dem Codesegment enthält weitere Informationen zu den Registrierungseintrag an.  
  
 In diesem Abschnitt finden Sie unter [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects].  
  
 Die erste GUID ist die CLSID für Projekte dieses Typs. die zweite GUID gibt an, den registrierten Projekttyp für die Vorlagen für Elemente hinzufügen.  
  
 \\{C061DB26-5833-11D2-96F5-000000000000} \AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000} \1  
  
 @="#6"  
  
 "TemplatesDir"="\<Visual Studio SDK-Installationspfad\\\VSIntegration\\\SomeFolder\\\SomePackage\\\SomeProject\\\SomeProjectItems"  
  
 "SortPriority" Dword:00000064 =  
  
|name|Typ|Daten (aus dem RGS-Datei)|Beschreibung|  
|----------|----------|-----------------------------|-----------------|  
|@ (Standard)|REG_SZ|#% IDS_ADDITEM_TEMPLATES_ENTRY %|Ressourcen-ID für **Element hinzufügen** Vorlagen.|  
|Val TemplatesDir|REG_SZ|%TEMPLATE_PATH%\ SomeProjectItems|Pfad der Projektelemente angezeigt, die im Dialogfeld für die **neues Element hinzufügen** Assistenten.|  
|Val SortPriority|REG_DWORD|100 ([!INCLUDE[vcprx64](../../includes/vcprx64-md.md)])|Bestimmt die Sortierreihenfolge im Knoten "Struktur" der Dateien angezeigt, der **neues Element hinzufügen** Dialogfeld.|  
  
> [!NOTE]
>  Die GUIDS für die Visual c# und Visual Basic-Projekttypen sind wie folgt:[!INCLUDE[csprcs](../../includes/csprcs-md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  
  
 Das Verzeichnis aufgeführt, für TemplateDirs, die % TEMPLATE_PATH%\SomeProjectItems ist, der Knoten auf der linken Seite des ist der **neues Element hinzufügen** Dialogfeld im Feld-Struktur. Zusätzliche Elemente in der Struktur basieren auf das Unterverzeichnis innerhalb dieses Stammverzeichnis. Die Dateien zum Projekt hinzugefügt werden sind die Elemente im Bereich rechts von der **neues Element hinzufügen** Dialogfeld.  
  
 Dieser Ordner wird in der Regel die Vorlagendateien für Ihr Projekt wie z. B. einer HTML-Vorlage oder cpp-Datei, und alle VSZ-Dateien zum Starten des Assistenten enthalten. Um zu steuern, wie die Elemente angezeigt werden, können Sie auch eine VSDIR-Dateien zum Lokalisieren von Verzeichnisnamen und Symbole einschließen. Die lokalisierte Zeichenfolge ist die Beschriftung, die Sie im Dialogfeld wird angezeigt, die diesem Knoten in der Struktur der neues Element hinzufügen-Dialogfeld darstellt.  
  
 Allerdings müssen Sie nicht alles in einer VSDIR-Datei haben. Sie können eine VSDIR-Datei für jedes Element in das Verzeichnis verwenden. Weitere Informationen finden Sie unter [Assistenten (. VSZ) Datei](../../extensibility/internals/wizard-dot-vsz-file.md) und [Vorlagenbeschreibung-Verzeichnis (. VSDIR)-Dateien](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
> [!NOTE]
>  Der VSDIR-Dateien in den Verzeichnissen der Vorlage sind optional. Sollten Sie einfach ein Projektelement im Verzeichnis eingefügt, und zeigt es im der **neues Element hinzufügen** im Dialogfeld können Sie diese Datei in dem in der TemplatesDir-Anweisung angegebenen Vorlagenverzeichnis ablegen. Die Datei wird dann im rechten Bereich angezeigt werden die **neues Element hinzufügen** im Dialogfeld für das betreffende Projekt. Wenn Sie eine lokalisierte Beschriftung für die Datei oder ein Symbol anzeigen möchten, müssen Sie allerdings mindestens eine VSDIR-Datei im Vorlagenverzeichnis einschließen.  
  
## <a name="grouping-project-items"></a>Gruppierung-Projektelemente  
 Wenn Vorlagengruppen in Ordnern im enthalten soll die **neues Element hinzufügen** Dialogfeld-Box-Struktur, benötigen Sie darin enthaltenen Unterverzeichnisse unter dem Stammverzeichnis für die Vorlage mit den Elementen. Wenn die **neues Element hinzufügen** im Dialogfeld für Benutzer angezeigt wird, wird auch die Unterordner und können sie Projektelemente aus.  
  
 Die Sortierpriorität im Codesegment bestimmt, in dem dieses Vorlagenverzeichnis in der Struktur relativ zu anderen Elementen des Strukturknotens erstellt wird. Für die **neues Element hinzufügen** im Dialogfeld die Sortierpriorität ist alles, was Sie enthalten müssen, damit die Elemente an der aktuellen Position im Dialogfeld angezeigt werden.  
  
 Sie können auch implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> Schnittstelle zum Filtern der Anzeige auf die **neues Element hinzufügen** Dialogfeld. Durch die Implementierung dieser Schnittstelle können Sie eine Vorlagenverzeichnis einrichten auf dem Datenträger, die enthält, z. B. 50 Dateien von Vorlage und Assistenten. Auf diese Weise haben Sie verschiedene Projekttypen mit 20 Dateien, die zu einem Projekttyp, andere 30 Dateien, die in einen anderen Projekttyp gehören und alle Dateien in einem allgemeinen Typ des Projekts gehören. Auf diese Weise kann je nach welchem Projekt Vorlage erstellt wurde, können Sie einen anderen Satz von Vorlagendateien anzeigen.  
  
 In einem Visual Basic-Projekt können Sie z. B. Webprojekte und Clientprojekte verfügen. Webformulare sind nicht nützlich, Elemente, die ein Clientprojekt hinzugefügt, und Windows Forms sind nicht nützlich, Elemente, die ein Web-Server-Projekt hinzugefügt. Aus diesem Grund können Sie ein Verzeichnis für Benutzervorlagen erstellen, die alle für beide Typen von Dateien enthält. Klicken Sie dann durch die Implementierung <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>, Sie können Elemente, die nicht angezeigt werden soll, basierend auf dem Typ des Projekts oder der projekteinstellungen im Projekt ausblenden.  
  
## <a name="filtering-project-items"></a>Filtern von Projektelementen  
 `IVsFilterAddProjectItemDlg2` bietet für das Filtern von Elementen in der Struktur (linker Bereich) und die Projektdateien (rechter Bereich) auf folgende Weise:  
  
- Durch den lokalisierten Namen (Beschriftungen, die das im Dialogfeld angezeigt, die in der VSDIR-Datei enthalten ist) gebotenen `IVsFilterAddProjectItemDlg`.  
  
- Durch die tatsächlichen Namen der Dateien und Ordner auf dem Datenträger (nicht lokalisierten — keine VSDIR-Datei) gebotenen `IVsFilterAddProjectItemDlg`.  
  
- Nach der Kategorie von bereitgestellten `IVsFilterAddProjectItemDlg2`.  
  
  Um nach Kategorie zu filtern, geben Sie eine Kategoriezeichenfolge, die ein Element in der VSDIR-Datei, z. B. "Webformular" oder "Client-Element" in Visual Basic. Der DialogfeldCode dann Ruft die Kategorie-Klassifizierung aus der VSDIR-Datei ab und übergibt sie an Sie. Sie können diese Informationen dann übergeben, für Ihre Implementierung der `IVsFilterAddProjectItemDlg2` zum Filtern der **neues Element hinzufügen** Dialogfeld nach Kategorien. Sie können auch Elemente für Webseiten oder als Client Win32-Anwendungsfällen filtern. Darüber hinaus können Sie identifizieren [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] mit Elementen Microsoft Foundation Classes (MFC) oder active-Vorlagenelementen Library (ATL) bezeichnet. Wenn Sie diese Elemente identifizieren, kann das Projektsystem einen eigenen Klassifizierungen definieren, sodass das System basierend auf Kategorien und Klassifizierungen gefiltert werden kann.  
  
  Wenn Sie diese Filter-Funktion implementieren, müssen Sie keine Tabelle mit jedem Element zugeordnet werden, die ausgeblendet werden soll. Sie können einfach klassifiziert Elemente in Typen und platzieren die Klassifizierungen in der VSDIR-Datei oder Dateien. Anschließend können Sie eines der Elemente ausblenden, die eine bestimmte Klassifizierung durch Implementieren der Schnittstelle. Auf diese Weise können Sie vornehmen, die Elemente in der **neues Element hinzufügen** Dialogfeld Feld dynamisch basierend auf den Zustand innerhalb des Projekts.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)   
 [CATIDs für Objekte, die in der Regel zum Erweitern von Projekten verwendet werden](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Beschreibung der Vorlage Verzeichnis (. VSDIR)-Dateien](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)

