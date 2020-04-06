---
title: Hinzufügen von Elementen zu den Dialogfeldern "Neue Elemente hinzufügen" | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af7f9e5c792785a23ad1674a50abeb4eb6d3cba9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710219"
---
# <a name="add-items-to-the-add-new-item-dialog-box"></a>Hinzufügen von Elementen zum Dialogfeld Neues Element hinzufügen
Der Vorgang zum Hinzufügen von Elementen zum Dialogfeld **Neues Element hinzufügen** beginnt mit den Registrierungsschlüsseln. Wie in den folgenden Registrierungseinträgen gezeigt, enthält der Abschnitt **AddItemTemplates** den Pfad und den Namen des Verzeichnisses, in dem Elemente, die im Dialogfeld Neues **Element** hinzufügen zur Verfügung gestellt werden, abgelegt werden.

> [!NOTE]
> Die Unmittelbar nach dem Codesegment folgende Tabelle enthält zusätzliche Informationen zum Registrierungseintrag.

 Dieser Abschnitt befindet sich unter **HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-14.0Exp-Projekte**.

 Die erste GUID ist die CLSID für Projekte dieses Typs; Die zweite GUID gibt den registrierten Projekttyp für die Vorlagen "Elemente hinzufügen" an:

 **\\C061DB26-5833-11D2-96F5-000000000000 \\AddItemTemplates\\TemplatesDir\\-ACEF4EB2-57CF-11D2-96F4-000000000000\\**

 **@**= #6

 **VorlagenDir** = \\&gt;\\&lt;&gt;\\&lt;&gt;\\&lt;\\&lt;&gt;\\Visual Studio SDK Installationspfad VSIntegration SomeFolder SomePackage SomeProject SomeProjectItems&lt;&gt;

 **SortPriority** = dword:00000064

| Name | type | Daten (aus *.rgs-Datei)* | BESCHREIBUNG |
|------------------|-----------| - | - |
| (Standard) | REG_SZ | %IDS_ADDITEM_TEMPLATES_ENTRY% | Ressourcen-ID für **Elementvorlagen hinzufügen.** |
| Val TemplatesDir | REG_SZ | %TEMPLATE_PATH%\\&lt;EinigeProjectItems&gt; | Pfad der Projektelemente, die im Dialogfeld für den Assistenten zum **Hinzufügen neuer Elemente** angezeigt werden. |
| Val SortPriority | REG_DWORD | 100[!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)]( ) | Bestimmt die Sortierreihenfolge im Strukturknoten von Dateien, die im Dialogfeld **Neues Element** hinzufügen angezeigt werden. |

> [!NOTE]
> Die GUIDS für die Projekttypen Visual C- und Visual Basic lauten wie folgt:
> - [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: FAE04EC0-301F-11D3-BF4B-00C04F79EFBC
> - [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: F184B08F-C81C-45F6-A57F-5ABD9991F28F

 Das für **TemplatesDir**aufgelistete Verzeichnis , *das %TEMPLATE_PATH%\\&lt;SomeProjectItems&gt;* ist, ist der Knoten auf der linken Seite der Dialogfeldstruktur **"Neues Element hinzufügen".** Zusätzliche Elemente in der Struktur basieren auf dem Unterverzeichnis in diesem Stammverzeichnis. Die Dateien, die dem Projekt hinzugefügt werden können, sind die Elemente im rechten Bereich des Dialogfelds **Neues Element hinzufügen.**

 In der Regel enthält dieser Ordner die Vorlagendateien für *.cpp* Ihr Projekt, z. B. eine HTML- oder CPP-Vorlagendatei, sowie alle *.vsz-Dateien* zum Starten von Assistenten. Um zu steuern, wie die Elemente angezeigt werden, können Sie auch *.vsdir-Dateien* zum Lokalisieren von Verzeichnisnamen und -symbolelementen einschließen. Die lokalisierte Zeichenfolge ist die Beschriftung, die im Dialogfeld angezeigt wird, das diesen Knoten im Dialogfeld-Fenster **"Neues Element hinzufügen"** darstellt.

 Sie müssen jedoch nicht alles in einer *.vsdir-Datei* haben. Sie können eine *.vsdir-Datei* für jedes Element im Verzeichnis haben. Weitere Informationen finden Sie unter [Wizard (.vsz)-Datei-](../../extensibility/internals/wizard-dot-vsz-file.md) und [Vorlagenverzeichnisbeschreibung (.vsdir)-Dateien](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

> [!NOTE]
> Die *.vsdir-Dateien* in den Vorlagenverzeichnissen sind optional. Wenn Sie nur ein Projektelement in das Verzeichnis einfügen und im Dialogfeld **Neues Element hinzufügen** anzeigen möchten, können Sie diese Datei in das Vorlagenverzeichnis einfügen, das in der **TemplatesDir-Anweisung** angegeben ist. Die Datei wird dann im rechten Bereich des Dialogfelds **Neues Element hinzufügen** für dieses Projekt angezeigt. Wenn Sie jedoch eine lokalisierte Beschriftung für die Datei oder ein Symbol anzeigen möchten, müssen Sie mindestens eine *.vsdir-Datei* in das Vorlagenverzeichnis aufnehmen.

## <a name="group-project-items"></a>Gruppieren von Projektelementen
 Wenn Sie Vorlagengruppen in Ordnern im Dialogfeld **"Neues Element hinzufügen"** enthalten möchten, müssen Sie Unterverzeichnisse unter dem Stammvorlagenverzeichnis mit den darin enthaltenen Elementen haben. Wenn den Benutzern das Dialogfeld **Neues Element hinzufügen** angezeigt wird, werden auch die Unterordner angezeigt und können daraus Projektelemente auswählen.

 Die Sortierpriorität im Codesegment bestimmt, wo dieses Vorlagenverzeichnis in der Struktur relativ zu anderen Elementen des Strukturknotens erstellt wird. Für das Dialogfeld **Neues Element hinzufügen** ist die Sortierpriorität alles, was Sie einschließen müssen, damit Ihre Elemente an der richtigen Position im Dialogfeld angezeigt werden.

 Sie können die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> Schnittstelle auch implementieren, um zu filtern, was im Dialogfeld **Neues Element hinzufügen** angezeigt wird. Durch Implementieren dieser Schnittstelle können Sie ein Vorlagenverzeichnis auf dem Datenträger einrichten, das z. B. 50 Vorlagen- und Assistentendateien enthält. Auf diese Weise können Sie verschiedene Projekttypen mit 20 Dateien haben, die zu einem Projekttyp gehören, die anderen 30 Dateien, die zu einem anderen Projekttyp gehören, und alle Dateien, die in einem allgemeinen Projekttyp verfügbar sind. Auf diese Weise können Sie je nach erstellter Projektvorlage einen anderen Satz von Vorlagendateien anzeigen.

 In einem Visual Basic-Projekt können Sie beispielsweise Webprojekte und Clientprojekte haben. Webformulare sind keine nützlichen Elemente, die einem Clientprojekt hinzugefügt werden können, und Windows-Formulare sind keine nützlichen Elemente, die einem Webserverprojekt hinzugefügt werden können. Daher können Sie ein Vorlagenverzeichnis erstellen, das alle Dateien für beide Projekttypen enthält. Durch Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>können Sie dann Elemente ausblenden, die nicht basierend auf dem Projekttyp oder den Projekteinstellungen im Projekt angezeigt werden sollen.

## <a name="filter-project-items"></a>Filtern von Projektelementen
 `IVsFilterAddProjectItemDlg2`sieht das Filtern von Elementen in der Struktur (linker Bereich) und Projektdateien (rechter Bereich) auf folgende Weise vor:

- Durch die lokalisierten Namen (Beschriftungen, die im Dialogfeld angezeigt werden, `IVsFilterAddProjectItemDlg`das in der *.vsdir-Datei* enthalten ist) von bereitgestellt.

- Durch die tatsächlichen Namen der Dateien und Ordner auf dem Datenträger (nicht `IVsFilterAddProjectItemDlg`lokalisiert — keine *.vsdir-Datei)* von zur Verfügung gestellt .

- Nach Kategorie, `IVsFilterAddProjectItemDlg2`bereitgestellt von .

  Um nach Kategorie zu filtern, geben Sie eine Kategoriezeichenfolge für ein Element in der *.vsdir-Datei* an, z. B. *Webformular* oder *Clientelement* in Visual Basic. Der Dialogfeldcode ruft dann die Kategorieklassifizierung aus der *.vsdir-Datei* ab und übergibt sie an Sie. Sie können diese Informationen dann `IVsFilterAddProjectItemDlg2` an Ihre Implementierung übergeben, um das Dialogfeld **Neues Element hinzufügen** nach Kategorien zu filtern. Sie können Elemente auch nach Webseiten oder als Win32-Anwendungsfälle des Clients filtern. Darüber hinaus können [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Sie markierte Elemente als Microsoft Foundation Classes (MFC) oder Active Template Library (ATL)-Elemente identifizieren. Wenn Sie diese Elemente identifizieren, kann das Projektsystem eigene Klassifizierungen definieren, sodass das System basierend auf Kategorien und Klassifizierungen gefiltert werden kann.

  Wenn Sie diese Filterfunktionalität implementieren, müssen Sie nicht jedes Element zuordnen, das ausgeblendet werden soll. Sie können Elemente einfach in Typen klassifizieren und die Klassifizierungen in die *.vsdir-Datei* oder Dateien setzen. Anschließend können Sie alle Elemente mit einer bestimmten Klassifizierung ausblenden, indem Sie die Schnittstelle implementieren. Auf diese Weise können Sie die Elemente im Dialogfeld **Neues Element hinzufügen** basierend auf dem Status innerhalb des Projekts dynamisch gestalten.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)
- [CATIDs für Objekte, die in der Regel zum Erweitern von Projekten verwendet werden](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
- [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Vorlagenverzeichnisbeschreibung (.vsdir)-Dateien](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
- [Wizarddatei (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
