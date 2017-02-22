---
title: "Hinzuf&#252;gen von Elementen, die zum Hinzuf&#252;gen neuer Elemente Dialogfelder | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Fügen Sie im Dialogfeld Neues Element, das Hinzufügen von Elementen"
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# Hinzuf&#252;gen von Elementen, die zum Hinzuf&#252;gen neuer Elemente Dialogfelder
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Das Verfahren zum Hinzufügen von Elementen der **Neues Element hinzufügen** Dialogfeld beginnt mit dem Registrierungsschlüssel. Siehe die folgenden Registrierungseinträge, Abschnitt AddItemTemplates enthält den Pfad und den Namen des Verzeichnisses in der Elemente, die in zur Verfügung gestellt der **Neues Element hinzufügen** Dialogfeld abgelegt werden.  
  
> [!NOTE]
>  Die Tabelle, die unmittelbar nach dem Codesegment enthält weitere Informationen zum Registrierungseintrag.  
  
 In diesem Abschnitt finden Sie unter \[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\14.0Exp\\Projects\].  
  
 Die erste GUID ist die CLSID für Projekte dieser Art. die zweite GUID gibt den registrierten Projekt für die Vorlagen Elemente hinzufügen.  
  
 \\{C061DB26\-5833\-11D2\-96F5\-000000000000}\\AddItemTemplates\\TemplateDirs\\ {ACEF4EB2\-57CF\-11D2\-96F4\-000000000000} \\1  
  
 @\="\#6"  
  
 "TemplatesDir"\="\< Visual Studio SDK\-Installation Path\\\\VSIntegration\\\\SomeFolder\\\\SomePackage\\\\SomeProject\\\\SomeProjectItems"  
  
 "SortPriority" \= Dword:00000064  
  
|Name|Typ|Daten \(.rgs\-Datei\)|Beschreibung|  
|----------|---------|---------------------------|------------------|  
|@ \(Standard\)|REG\_SZ|\#% IDS\_ADDITEM\_TEMPLATES\_ENTRY %|Ressourcen\-ID für **Hinzufügen** Vorlagen.|  
|Val TemplatesDir|REG\_SZ|%TEMPLATE\_PATH%\\ SomeProjectItems|Pfad der Projektelemente angezeigt, die im Dialogfeld für die **Neues Element hinzufügen** Assistenten.|  
|Val SortPriority|REG\_DWORD|100 \([!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)]\)|Bestimmt die Sortierreihenfolge im Strukturknoten der Dateien angezeigt, der **Neues Element hinzufügen** \(Dialogfeld\).|  
  
> [!NOTE]
>  Die GUIDS für die Visual C\#\- und Visual Basic\-Typen sind wie folgt:[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0\-301F\-11D3\-BF4B\-00C04F79EFBC}[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F\-C81C\-45F6\-A57F\-5ABD9991F28F}  
  
 Das Verzeichnis aufgeführt, für TemplateDirs, d. h. % TEMPLATE\_PATH%\\SomeProjectItems, auf der linken Seite des Knotens ist die **Neues Element hinzufügen** Dialogfeld Feld Struktur. Zusätzliche Elemente in der Struktur basieren auf das Unterverzeichnis in das Root\-Verzeichnis. Die Dateien zum Projekt hinzugefügt werden, sind die Elemente im rechten Bereich von der **Neues Element hinzufügen** \(Dialogfeld\).  
  
 Dieser Ordner wird in der Regel die Vorlagendateien für das Projekt z. B. eine HTML\-Vorlage oder cpp\-Datei und alle VSZ\-Dateien zum Starten des Assistenten enthalten. Um zu steuern, wie die Elemente angezeigt werden, können Sie auch eine VSDIR\-Dateien für die Lokalisierung von Verzeichnis\- und Symbole einschließen. Die lokalisierte Zeichenfolge ist die Beschriftung, die im Dialogfeld angezeigt wird, die dieser Knoten in das Dialogfeld Neues Element hinzufügen\-Struktur darstellt.  
  
 Allerdings müssen Sie keinen haben alles in einer VSDIR\-Datei. Sie können eine VSDIR\-Datei für jedes Element im Verzeichnis haben. Weitere Informationen finden Sie unter [Assistenten \(. VSZ\)\-Datei](../../extensibility/internals/wizard-dot-vsz-file.md) und [Beschreibung der Vorlage Verzeichnis \(. VSDIR\)\-Dateien](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
> [!NOTE]
>  VSDIR\-Dateien in den Verzeichnissen Vorlage sind optional. Wenn soll nur legen Sie ein Projektelement im Verzeichnis und in den **Neues Element hinzufügen** im Dialogfeld können Sie die Datei legen Sie im Vorlagenverzeichnis in der TemplatesDir\-Anweisung angegeben. Die Datei wird dann im rechten Bereich angezeigt werden die **Neues Element hinzufügen** im Dialogfeld für das Projekt. Wenn Sie eine lokalisierte Beschriftung für die Datei oder ein Symbol anzeigen möchten, müssen Sie mindestens eine VSDIR\-Datei im Vorlagenverzeichnis einschließen.  
  
## Gruppierung von Projektelementen  
 Wenn Vorlagengruppen in Ordnern enthalten soll die **Neues Element hinzufügen** Dialogfeld Feld Struktur benötigen Sie in diese Unterverzeichnisse unter dem Stammverzeichnis für die Vorlage mit den Elementen. Wenn die **Neues Element hinzufügen** im Dialogfeld für Benutzer angezeigt wird, die sie auch die Unterordner und können sie Projektelemente aus.  
  
 Die Sortierpriorität in das Codesegment bestimmt, in dem dieses Verzeichnis in der Struktur relativ zu anderen Elementen des Strukturknotens erstellt wird. Für die **Neues Element hinzufügen** klicken Sie im Dialogfeld die Sortierpriorität ist alles, die eingeschlossen werden muss, damit die Elemente in den richtigen Speicherort im Dialogfeld angezeigt werden.  
  
 Sie können auch implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> Schnittstelle zum Filtern der angezeigten Daten im der **Neues Element hinzufügen** \(Dialogfeld\). Durch die Implementierung dieser Schnittstelle können Sie eine Vorlagenverzeichnis einrichten auf Datenträger,, z. B. enthält, 50\-Vorlage und die Assistenten\-Dateien. Auf diese Weise haben Sie verschiedene Projekttypen mit 20 Dateien, die einen Projekttyp, die 30 Dateien, die zu einem anderen Projekttyp gehören und alle Dateien in einen allgemeinen Typ von Projekt gehören. Auf diese Weise kann je nach dem Projektmanager Vorlage erstellt wurde, können Sie einen anderen Satz von Vorlagendateien anzeigen.  
  
 In einem Visual Basic\-Projekt können Sie z. B. Webprojekte und Clientprojekte verfügen. Web Forms sind nicht nützlich, Elemente, die ein Clientprojekt hinzugefügt, und Windows Forms nicht nützlich, Elemente, die ein Web\-Server\-Projekt hinzugefügt. Daher können Sie ein Verzeichnis erstellen, die alle Dateien für beide Typen des Projekts enthält. Klicken Sie dann durch die Implementierung <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>, Sie können Elemente, die nicht angezeigt werden soll, basierend auf dem Typ des Projekts oder projekteinstellungen im Projekt ausblenden.  
  
## Filtern von Projektelementen  
 `IVsFilterAddProjectItemDlg2` enthält zum Filtern von Elementen in der Struktur \(linker Fensterbereich\) und die Projektdateien \(rechter Bereich\) auf folgende Weise:  
  
-   Nach den lokalisierten Namen \(Beschriftungen, die in der VSDIR\-Datei enthalten sind, wird im Dialogfeld angezeigt\), die von bereitgestellten `IVsFilterAddProjectItemDlg`.  
  
-   Durch die tatsächlichen Namen der Dateien und Ordner auf dem Datenträger \(nicht lokalisierten – keine VSDIR\-Datei\) von bereitgestellten `IVsFilterAddProjectItemDlg`.  
  
-   Nach der Kategorie von bereitgestellten `IVsFilterAddProjectItemDlg2`.  
  
 Um nach Kategorie zu filtern, geben Sie eine Kategoriezeichenfolge, die ein Element in der VSDIR\-Datei, z. B. "Webformular" oder "Client\-Item" in Visual Basic. DialogfeldCode Ruft die Kategorie Klassifizierung von VSDIR\-Datei ab und übergibt sie an Sie. Anschließend können Sie diese Informationen übergeben, um die Implementierung von `IVsFilterAddProjectItemDlg2` zum Filtern der **Neues Element hinzufügen** Dialogfeld nach Kategorien. Sie können Elemente auch filtern, Webseiten oder als Client Win32\-Anwendungsfällen. Darüber hinaus können Sie identifizieren [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Elemente als Microsoft Foundation Classes \(MFC\) oder aktiven Vorlage Library \(ATL\) Elemente markiert. Wenn Sie diese Elemente identifiziert, kann das Projektsystem eigene Klassifikationen definieren, sodass das System anhand von Kategorien und Klassifikationen gefiltert werden kann.  
  
 Wenn Sie diese Filterfunktionalität implementieren, müssen Sie keine Tabelle jedes Elements zuordnen, die ausgeblendet werden soll. Einfach können Sie Elemente in Typen klassifizieren und Klassifikationen in der VSDIR\-Datei oder Dateien abgelegt. Dann können Sie eines der Elemente ausblenden, die eine bestimmte Klassifizierung durch Implementieren der Schnittstelle haben. Auf diese Weise können Sie machen die Elemente in der **Neues Element hinzufügen** Dialogfeld Feld dynamisch basierend auf den Status innerhalb des Projekts.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Registrieren von Projekt\- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)   
 [CATIDs für Objekte, die in der Regel verwendet werden, um Projekte zu erweitern.](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [Hinzufügen von Projekt\- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Beschreibung der Vorlage Verzeichnis \(. VSDIR\)\-Dateien](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [Assistenten \(. VSZ\)\-Datei](../../extensibility/internals/wizard-dot-vsz-file.md)