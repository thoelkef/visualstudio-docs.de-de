---
title: Hinzufügen von Elementen zu den Dialog Feldern "Neues Element hinzufügen" | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ecdacfc4ac65e0dc18512bfb56eb870545c66a9b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840922"
---
# <a name="adding-items-to-the-add-new-item-dialog-boxes"></a>Hinzufügen von Elementen zu den Dialogfeldern „Neues Element hinzufügen“
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Der Prozess zum Hinzufügen von Elementen zum Dialogfeld **Neues Element hinzufügen** wird mit den Registrierungs Schlüsseln gestartet. Wie in den folgenden Registrierungs Einträgen gezeigt, enthält der Abschnitt additemtemplates den Pfad und den Namen des Verzeichnisses, in dem die im Dialogfeld **Neues Element hinzufügen** verfügbaren Elemente abgelegt werden.  
  
> [!NOTE]
> Die Tabelle, die direkt auf das Codesegment folgt, enthält weitere Informationen zum Registrierungs Eintrag.  
  
 Dieser Abschnitt befindet sich unter [HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\14.0exp\projects].  
  
 Die erste GUID ist die CLSID für Projekte dieses Typs. die zweite GUID gibt den registrierten Projekttyp für die Vorlagen zum Hinzufügen von Elementen an.  
  
 \\{C061DB26-5833-11d2-96F5-000000000000} \additemtemplates\templatedirs\ {ACEF4EB2-57CF-11d2-96F4-000000000000} \ 1  
  
 @ = "#6"  
  
 "Templatesdir" = " \< Visual Studio SDK-Installationspfad \\ \vsintegration \\ \somefolder \\ \somepackage \\ \someproject \\ \someprojectitems"  
  
 "SortPriority" = DWORD: 00000064  
  
|Name|type|Daten (aus RGS-Datei)|BESCHREIBUNG|  
|----------|----------|-----------------------------|-----------------|  
|@ (Standard)|REG_SZ|#% IDS_ADDITEM_TEMPLATES_ENTRY%|Ressourcen-ID für **Element Vorlagen hinzufügen** .|  
|Val templatesdir|REG_SZ|% TEMPLATE_PATH% \ Someprojectitems|Der Pfad der Projekt Elemente, die im Dialogfeld für den Assistenten zum **Hinzufügen eines neuen Elements** angezeigt werden.|  
|Val SortPriority|REG_DWORD|100 ( [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)] )|Bestimmt die Sortierreihenfolge im Struktur Knoten von Dateien, die im Dialogfeld **Neues Element hinzufügen** angezeigt werden.|  
  
> [!NOTE]
> Die GUIDs für die Visual c#-und Visual Basic-Projekttypen lauten wie folgt: [!INCLUDE[csprcs](../../includes/csprcs-md.md)] {FAE04EC0-301F-11d3-BF4B-00C04F79EFBC} [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] : {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  
  
 Das für templatedirs (% TEMPLATE_PATH% \ someprojectitems) aufgelistete Verzeichnis ist der Knoten auf der linken Seite der Struktur des Dialog Felds **Neues Element hinzufügen** . Zusätzliche Elemente in der Struktur basieren auf dem Unterverzeichnis innerhalb dieses Stamm Verzeichnisses. Die Dateien, die dem Projekt hinzugefügt werden können, sind die Elemente im rechten Bereich des Dialog Felds **Neues Element hinzufügen** .  
  
 In der Regel enthält dieser Ordner die Vorlagen Dateien für das Projekt, z. b. eine Vorlagen-HTML oder eine CPP-Datei und alle VSZ-Dateien zum Starten von Assistenten. Um zu steuern, wie die Elemente angezeigt werden, können Sie auch VSDIR-Dateien zum Lokalisieren von Verzeichnisnamen und Symbolen einschließen. Die lokalisierte Zeichenfolge ist die Beschriftung, die im Dialogfeld angezeigt wird, das diesen Knoten im Dialogfeld Neues Element hinzufügen darstellt.  
  
 Allerdings müssen Sie nicht alles in einer VSDIR-Datei haben. Eine VSDIR-Datei kann für jedes Element im Verzeichnis vorhanden sein. Weitere Informationen finden Sie unter [Wizard (. VSZ-Datei](../../extensibility/internals/wizard-dot-vsz-file.md) -und [Vorlagen Verzeichnis Beschreibung (. VSDIR-Dateien](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
> [!NOTE]
> Die VSDIR-Dateien in den Vorlagen Verzeichnissen sind optional. Wenn Sie nur ein Projekt Element in das Verzeichnis einfügen und im Dialogfeld **Neues Element hinzufügen** anzeigen möchten, können Sie diese Datei in das Vorlagen Verzeichnis einfügen, das in der templatesdir-Anweisung angegeben ist. Die Datei wird dann im rechten Bereich des Dialog Felds **Neues Element hinzufügen** für das Projekt angezeigt. Wenn Sie jedoch eine lokalisierte Beschriftung für die Datei oder ein Symbol anzeigen möchten, müssen Sie mindestens eine VSDIR-Datei in das Verzeichnis "Templates" einschließen.  
  
## <a name="grouping-project-items"></a>Gruppieren von Projekt Elementen  
 Wenn Sie Vorlagen Gruppen in Ordnern in der Struktur des Dialog Felds **Neues Element hinzufügen** möchten, müssen Sie Unterverzeichnisse unter dem Stamm Vorlagen Verzeichnis mit den darin enthaltenen Elementen enthalten. Wenn Benutzern das Dialogfeld **Neues Element hinzufügen** angezeigt wird, sehen Sie auch die Unterordner und können Projekt Elemente aus ihnen auswählen.  
  
 Die Sortier Priorität im Codesegment bestimmt, wo das Vorlagen Verzeichnis in der Struktur relativ zu anderen Elementen des Struktur Knotens erstellt wird. Im Dialogfeld **Neues Element hinzufügen** müssen Sie nur die Sortier Priorität einschließen, damit die Elemente an der richtigen Position im Dialogfeld angezeigt werden.  
  
 Sie können auch die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> Schnittstelle implementieren, um zu filtern, was im Dialogfeld **Neues Element hinzufügen** angezeigt wird. Durch Implementieren dieser Schnittstelle können Sie ein Vorlagen Verzeichnis auf dem Datenträger einrichten, das z. b. 50-Vorlagen-und Assistenten Dateien enthält. Auf diese Weise können Sie unterschiedliche Projekttypen mit 20 Dateien haben, die zu einem Projekttyp gehören, die anderen 30 Dateien, die zu einem anderen Projekttyp gehören, sowie alle Dateien, die in einem allgemeinen Projekttyp verfügbar sind. Auf diese Weise können Sie, je nachdem, welche Projektvorlage erstellt wird, einen anderen Satz von Vorlagen Dateien anzeigen.  
  
 Beispielsweise können Sie in einem Visual Basic Projekt über Webprojekte und Client Projekte verfügen. Webformulare sind keine nützlichen Elemente, die einem Client Projekt hinzugefügt werden können, und Windows Forms sind keine nützlichen Elemente, die einem Webserver Projekt hinzugefügt werden können. Daher können Sie ein Vorlagen Verzeichnis erstellen, in dem alle Dateien für beide Projekttypen enthalten sind. Anschließend können Sie durch Implementieren von <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> Elemente ausblenden, die nicht auf der Grundlage des Typs der Projekt-oder Projekteinstellungen im Projekt angezeigt werden sollen.  
  
## <a name="filtering-project-items"></a>Filtern von Projekt Elementen  
 `IVsFilterAddProjectItemDlg2` ermöglicht das Filtern von Elementen in der Struktur (linker Bereich) und den Projektdateien (rechter Bereich) auf folgende Weise:  
  
- Nach den lokalisierten Namen (Beschriftungen, die im Dialogfeld angezeigt werden, das in der VSDIR-Datei enthalten ist), das von bereitgestellt wird `IVsFilterAddProjectItemDlg` .  
  
- Durch die tatsächlichen Namen der Dateien und Ordner auf dem Datenträger (nicht lokalisierte – No. VSDIR-Datei), die von bereitgestellt werden `IVsFilterAddProjectItemDlg` .  
  
- Nach Kategorie, bereitgestellt von `IVsFilterAddProjectItemDlg2` .  
  
  Um nach Kategorie zu filtern, geben Sie eine Kategoriezeichenfolge für ein Element in der VSDIR-Datei an, z. b. "Web Form" oder "Client Element" in Visual Basic. Der Dialogfeld Code ruft dann die Kategorieinformationen aus der VSDIR-Datei ab und übergibt sie an Sie. Sie können diese Informationen dann an die Implementierung von übergeben `IVsFilterAddProjectItemDlg2` , um das Dialogfeld **Neues Element hinzufügen** nach Kategorien zu filtern. Sie können auch Elemente für Webseiten oder Win32-Client Anwendungsfälle filtern. Außerdem können Sie [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] markierte Elemente als Microsoft Foundation Classes (MFC) oder als ATL-Elemente (Active Template Library) identifizieren. Wenn Sie diese Elemente identifizieren, kann das Projekt systemeigene Klassifizierungen definieren, damit das System anhand von Kategorien und Klassifizierungen gefiltert werden kann.  
  
  Wenn Sie diese Filter Funktionalität implementieren, müssen Sie nicht jedes Element, das ausgeblendet werden soll, eine Tabelle zuordnen. Sie können Elemente einfach in Typen klassifizieren und die Klassifizierungen in der VSDIR-Datei oder in Dateien platzieren. Anschließend können Sie alle Elemente mit einer bestimmten Klassifizierung ausblenden, indem Sie die-Schnittstelle implementieren. Auf diese Weise können Sie die Elemente im Dialogfeld **Neues Element hinzufügen** dynamisch festlegen, basierend auf dem Status innerhalb des Projekts.  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Registrieren von Projekt-und Element Vorlagen](../../extensibility/internals/registering-project-and-item-templates.md)   
 [CATIDs für Objekte, die in der Regel zum Erweitern von Projekten verwendet werden](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [Hinzufügen von Projekt-und Projekt Element Vorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Beschreibung des Vorlagen Verzeichnisses (. VSDIR-Dateien](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)
