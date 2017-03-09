---
title: "Erstellen von benutzerdefinierten Aufgabenlistenansichten | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Aufgabenliste, benutzerdefinierte Ansichten"
ms.assetid: c25f8f5d-55a1-4b5e-b617-3d1140bcb98a
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# Erstellen von benutzerdefinierten Aufgabenlistenansichten
Sie können eine benutzerdefinierte Aufgabenliste in Visual Studio anzeigen, indem Sie eine benutzerdefinierte Ansicht der Aufgabenliste erstellen.  
  
 Verwenden Sie die Registrierung, um eine benutzerdefinierte Ansicht zu erstellen und diese Angaben zu machen:  
  
-   Die Spalten  
  
-   Die Sortierreihenfolge für die Spalten  
  
-   Die Standardsortierreihenfolge  
  
-   Kategorien für Aufgaben, die angezeigt werden soll  
  
 Sie können eine benutzerdefinierte Kategorie CAT\_ALL für mehrere Kategorien anzeigen oder angeben.  Sie können benutzerdefinierte Text auch Spalten erstellen, die Text enthalten.  Allerdings können Sie benutzerdefinierten Text nicht auf Spalten sortieren.  
  
 In den folgenden Tabellen werden im Registrierungsformat für benutzerdefinierte Ansichten der Aufgabenliste angezeigt.  
  
 In jedem der Tabellen, ist *GEGEN Reg\-Stamm* gleich HKEY\_LOCAL\_MACHINE \\ Software \\ Microsoft \\ VisualStudio \\ 8.0 \\.  Die Tabellen stellen die Einträge für Skripts und zusätzliche Informationen für jede Registrierung Statement bereit.  
  
 \[*GEGEN Reg\-Stamm*TaskList Ordner Views \\ \\. \\*GUID*\]  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|---------|-------------|------------------|  
|Name|REG\_SZ|Text|STRING\-Name der Ansicht oder \#xxx.<br /><br /> Der Name kann z. B. eine normale Zeichenfolge „My benutzerdefinierte Ansicht“ sein, oder es kann eine Ressourcenzeichenfolge in einem Paket \(\#xxx\) sein.|  
|Package|REG\_SZ|Text|\[entscheiden Sie\], Zeichenfolgendarstellung von GUIDs.  Dies ist erforderlich, wenn einige Ressourcenzeichenfolgen Zeichenfolgen \(\#xxx\) befinden. andernfalls wird es ignoriert.|  
  
 \[*GEGEN Reg\-Stamm*TaskList Ordner Views \\ \\. \\ \\. \\*GUID*Spalten*Zahl*\]  
  
> [!NOTE]
>  *Zahl* Basis 1 ist die Reihenfolge der Spalten in der Sicht \(wobei 1 die am weitesten links stehende Spalte ist\).  Weitere Spalten Inkrement *Zahl*.  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|---------|-------------|------------------|  
|Feld|REG\_DWORD||<xref:Microsoft.VisualStudio.Shell.Interop.VSTASKFIELD> , das das Feld der Spalte befindet.|  
|Breite|REG\_DWORD||Optional.  Die Breite der Spalte in Pixel.  Wenn die Spalte nicht wesentlich ist, wird dieser Parameter ignoriert.|  
|Index|REG\_DWORD||Optional.  Wenn das Feld FLD\_CUSTOM ist, ist dies der benutzerdefinierte Spaltenindex.|  
|Name|REG\_SZ|Text|IF\-Feld ist FLD\_CUSTOM, dies ist der Name der benutzerdefinierten Spalte.<br /><br /> Name kann eine Ressourcenzeichenfolge in \#xxx Format werden.|  
|Filter|REG\_SZ oder REG\_DWORD||Entweder ein DWORD, das die integrierten VSTASKCATEGORY oder STRING aufweist, die die GUID einer benutzerdefinierten Kategorie darstellt.|  
  
 \[*GEGEN Reg\-Stamm*TaskList Ordner Views \\ \\. \\ \\*GUID*Sortierung \\*Zahl*\]  
  
> [!NOTE]
>  *Zahl* identifiziert den Sortierschlüssel.  Zum Beispiel für den primären Sortierschlüssel, *Zahl* ist gleich 1.  Für den sekundären Sortierschlüssel entspricht *Zahl* 2 usw.  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|---------|-------------|------------------|  
|Feld|REG\_DWORD||<xref:Microsoft.VisualStudio.Shell.Interop.VSTASKFIELD> , das das Feld der Spalte befindet.|  
|Index|REG\_DWORD||Optional.  Wenn das Feld FLD\_CUSTOM ist, ist dies der benutzerdefinierte Spaltenindex.|  
  
 Um eine benutzerdefinierte Spalte zu implementieren, müssen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2>\-Schnittstelle für den Aufgabenelementen implementieren, und Sie müssen die folgenden Methoden für diese Schnittstelle implementieren:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2.get_CustomColumnText%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2.put_CustomColumnText%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2.IsCustomColumnReadOnly%2A>  
  
 Bei Bedarf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2> Implementierung fragt die Aufgabenliste mithilfe einer benutzerdefinierten Spaltennummer von einer bestimmten Ansicht, dargestellt durch *einige guid*.  Wenn die Aufgabe die entsprechenden Informationen über diese Spalte in dieser Sicht enthält, geben Sie Informationen an diese Spalte und geben an, ob dieser Text schreibgeschützt ist.  
  
## Siehe auch  
 [Gewusst wie: Erstellen benutzerdefinierter Kategorien von Aufgabenlisten](../misc/how-to-create-custom-categories-of-task-lists.md)