---
title: "Registrieren eine &#228;ltere Sprache Service2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Registrierung, Dienste für Sprachen"
  - "Language Services, Informationen in der Registrierung"
  - "Sprachdienste-Registrierung"
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# Registrieren einer Legacy-Sprachdienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die folgenden Abschnitte enthalten Listen der Registrierungseinträge für die verschiedenen Sprache\-Service in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 In der folgenden Liste von Registrierungseinträgen *Stamm der VS\-Reg* gleich HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*X.Y*, wobei *X.Y* ist die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Versionsnummer.  
  
## Registrierungseinträge für Language Service\-Optionen  
 Die *Stamm der VS\-Reg*\\Languages\\Language Services\\*Sprachenname* Schlüssel kann die folgenden Werte enthalten.  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|---------|-------------|------------------|  
|\(Standard\)|REG\_SZ|*\< GUID \>*|Die GUID des Sprachdiensts.|  
|LangResID|REG\_DWORD|0 x 0 – 0xffff|Eine Zeichenfolge Ressourcenbezeichner \(ResID\) für den lokalisierten Textname der Sprache.|  
|Package|REG\_SZ|*\< GUID \>*|Die GUID des VSPackage.|  
|ShowCompletion|REG\_DWORD|0\-1|Gibt an, ob die **Anweisungsabschluss** Optionen in der **Optionen** Dialogfeld aktiviert sind.|  
|ShowSmartIndent|REG\_DWORD|0\-1|Gibt an, ob die Option zur Auswahl **Smart** Einzug den **Optionen** Dialogfeld aktiviert ist.|  
|RequestStockColors|REG\_DWORD|0\-1|Gibt an, ob benutzerdefinierte oder Standardfarben verwendet, um die Farbe für Schlüsselwörter.|  
|ShowHotURLs|REG\_DWORD|0\-1|Gibt an, ob der Benutzer, URLs klicken kann.|  
|Standardmäßig nicht bei laufendem Betrieb URLs|REG\_DWORD|0\-1|Gibt die ursprüngliche Einstellung für die **einfaches Klicken für URLs aktivieren** \-Option in der **Optionen** \(Dialogfeld\).|  
|DefaultToInsertSpaces|REG\_DWORD|0\-1|Gibt an, ob der Sprachdienst "Leerzeichen einfügen" die Option als Standard Registerkarte hat.|  
|ShowDropdownBarOption|REG\_DWORD|0\-1|Aktiviert oder deaktiviert die **Navigationsleiste** \-Option in der **Optionen** im Dialogfeld, das Anzeigen oder Ausblenden der **Navigationsleiste**.|  
|Nur einzelne Codefenster|REG\_DWORD|0\-1|Aktiviert oder deaktiviert die **Neues Fenster** Choice in der **Fenster** Menü für einen Sprachdienst.|  
|EnableAdvancedMembersOption|REG\_DWORD|0\-1|Aktiviert oder deaktiviert eine **Optionen** Einstellung der im Dialogfeld für **Erweiterte Member ausblenden**.|  
|Unterstützung für CF\_HTML|REG\_DWORD|0\-1|Gibt an, ob der Editor ermöglicht, kopieren und Einfügen von HTML\-Daten.|  
|EnableLineNumbersOption|REG\_DWORD|0\-1|Gibt an, ob die **Zeilennummern** Optionen in der **Optionen** im Dialogfeld für eine Sprachdienst aktiviert ist.|  
|HideAdvancedMembersByDefault|REG\_DWORD|0\-1|Gibt an, ob erweiterte Member wie z. B. private Felder in Vervollständigungslisten ausgeblendet werden.|  
|ShowBraceCompletion|REG\_DWORD|0\-1|Gibt an, ob die **geschweiften Klammer abgeschlossen** \-Option in der **Optionen** Dialogfeld aktiviert ist.|  
  
### Beispiel  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        (Default)             = reg_sz:{B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
        LangResID             = reg_dword:0x00000000  
        Package               = reg_sz:{8C2EA640-ABC1-11D0-9D62-00C04FD9DFD9}  
        ShowCompletion        = reg_dword:0x00000001  
        ShowSmartIndent       = reg_dword:0x00000001  
        ShowDropdownBarOption = reg_dword:0x00000001  
```  
  
## Registrierungseinträge für Sprachen\-Debugger\-Optionen  
 Die *Stamm der VS\-Reg*\\Languages\\Language Services\\*Sprachenname*\\Debugger Languages\\*GUID*\\ Schlüssel kann die folgenden Werte enthalten.  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|---------|-------------|------------------|  
|\(Standard\)|REG\_SZ|Text|Der Standardwert kann verwendet werden, um den Namen der Sprache zu dokumentieren. Der Name des Schlüssels ist eine GUID, der eine Auswertung eines Ausdrucks, der einen entsprechenden Eintrag in *\< VS Reg Root \>*\\AD7Metrics\\Expression Auswertung.|  
  
### Beispiel  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        Debugger Languages\  
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\  
            (Default) = reg_sz:C++  
```  
  
## Registrierungseinträge für Editor\-Optionen  
 Sie können Registrierungsschlüssel unter dem Schlüssel EditorToolsOptions für Eigenschaftenseiten und die Eigenschaftsknoten hinzufügen. Diese Schlüssel und deren Werte identifizieren Eigenschaftenseiten in der **Optionen** \(Dialogfeld\) \(auf der **Tools** Menü\) zum Konfigurieren des Sprachdiensts verwendet werden. Im folgenden Beispiel *Seitennamen* ist der Name einer Eigenschaftenseite und *Knotenname* ist der Name eines Knotens in der Struktur auf der **Optionen** \(Dialogfeld\). Die Seite Eintrag und der Knoten\-Eintrag müssen separat angegeben werden.  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|---------|-------------|------------------|  
|\(Standard\)|REG\_SZ|ResID|Der lokalisierte Anzeigename von dieser Seite. Der Name kann Literaltext oder`nnn`, wobei `nnn` ist eine String\-Ressourcen\-ID in der Satelliten\-DLL des angegebenen VSPackage.|  
|Package|REG\_SZ|*GUID*|Die GUID des VSPackage, das dieser Seite implementiert.|  
|Seite|REG\_SZ|*GUID*|Die GUID der Eigenschaftenseite zum Anfordern von VSPackages durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> Methode. Wenn dieser Registrierungseintrag nicht vorhanden ist, beschreibt der Registrierungsschlüssel einen Knoten, der nicht auf einer Seite.|  
  
### Beispiel  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      CSharp\  
        EditorToolsOptions\  
          Formatting\  
            (Default) = reg_sz:#242  
            Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
            General\  
              (Default) = reg_sz:#255  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{3EB2CC0B-033E-4D75-B26A-B2362C25227E}  
            Indentation\  
              (Default) = reg_sz:#250  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{5E21D017-6D2A-4114-A1F1-C923F001CBBB}  
            Newlines\  
              (Default) = reg_sz:#253  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{607D8062-68D1-41E4-9A35-B5E7F14D0481}  
```  
  
## Registrierungseinträge für Dateinamenoptionen\-Erweiterung  
 Der Eintrag für die Erweiterung sollte den vorangestellten Punkt, z. B. ".myext" enthalten.  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|---------|-------------|------------------|  
|\(Standard\)|REG\_SZ|*GUID*|Dienst\-GUID für den Standarddienst für die Sprache für diese Erweiterung Dateinamentyp.|  
  
### Beispiel  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    File Extensions\  
      .cpp\  
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
```  
  
## Registrierungseinträge für Editoroptionen  
 Die *Stamm der VS\-Reg*\\Editors Schlüssel kann die folgenden Werte enthalten:  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|---------|-------------|------------------|  
|\(Standard\)|REG\_SZ|""|Nicht verwendet; Sie können hier Ihren Namen ein, für die Dokumentation einfügen.|  
|DefaultToolboxTab|REG\_SZ|""|Der Name der Toolboxregisterkarte als Standard festlegen, wenn der Editor aktiv ist.|  
|DisplayName|REG\_SZ|ResID|Anzuzeigenden Namen die **Öffnen mit** \(Dialogfeld\). Der Name ist die Zeichenfolgenressource\-ID oder ein Name im Standardformat.|  
|ExcludeDefTextEditor|REG\_DWORD|0\-1|Verwendet für die **Öffnen mit** Menübefehl. Wenn Sie nicht die Standard\-Text\-Editor in der Liste der verfügbaren Editoren für einen bestimmten Dateityp auflisten möchten, legen Sie diesen Wert auf 1 fest.|  
|LinkedEditorGUID|REG\_SZ|*\< GUID \>*|Verwendet für jede Sprachdienst, der mit Codepage\-Unterstützung die Datei öffnen kann. Z. B. Wenn Sie öffnen eine TXT\-Datei mithilfe der **Öffnen mit** Befehl Optionen für die Verwendung der Quellcode\-Editor mit und ohne Codierung bereitgestellt werden.<br /><br /> Die GUID, die Namen der Unterschlüssel angegeben ist, für die Codepage\-Editor\-Factory. in diesem bestimmten Registrierungseintrag angegebene verknüpfte GUID ist für die reguläre Editorfactory. Der Zweck dieses Eintrags ist, wenn die IDE keine Datei mit dem Standardeditor öffnen, die IDE versucht, den nächsten\-Editor in der Liste zu verwenden. Dieser nächsten Editor darf nicht der Codepage\-Editor\-Factory sein, da diese Factory\-Editors im Grunde die Editorfactory entspricht, die nicht.|  
|Package|REG\_SZ|*\< GUID \>*|VSPackage\-GUID für den Anzeigenamen ResID.|  
  
### Beispiel  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      (Default)            = reg_sz:Html Editor with Encoding  
      DefaultToolboxTab    = reg_sz:HTML  
      DisplayName          = reg_sz:#20101  
      LinkedEditorGUID     = reg_sz:{C76D83F8-A489-11D0-8195-00A0C91BBEE3}  
      Package              = reg_sz:{1B437D20-F8FE-11D2-A6AE-00104BCC7269}  
```  
  
## Registrierungseinträge für logische Ansicht\-Optionen  
 Die *Stamm der VS\-Reg*\\Editors\\*GUI\-Editor \>*\\LogicalViews Schlüssel kann die folgenden Werte enthalten.  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|---------|-------------|------------------|  
|\(Standard\)|REG\_SZ||Nicht verwendet.|  
|*\< GUID \>*|REG\_SZ|""|Der Schlüssel, die den logischen Ansichten unterstützt. Sie können beliebig viele verwenden, wie Sie benötigen. Der Name des Registrierungseintrags ist von Bedeutung, nicht den Wert, der immer eine leere Zeichenfolge ist.|  
  
### Beispiel  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      LogicalViews\  
       (Default) = reg_sz:  
       {7651a700-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a701-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a702-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a703-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
```  
  
## Registrierungseinträge für Editor\-Erweiterung  
 Die *Stamm der VS\-Reg*\\Editors\\*\-Editor\-GUID*\\Extensions Schlüssel kann die folgenden Werte enthalten. Die Erweiterung umfasst nicht den vorangestellten Punkt.  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|---------|-------------|------------------|  
|\(Standard\)|REG\_SZ||Nicht verwendet.|  
|*\< Erweiterung \>*|REG\_DWORD|0\-0xffffffff|Relative Priorität der Erweiterungen. Wenn zwei oder mehr Sprachen gemeinsam die gleiche Erweiterung verwenden, wird die Sprache höherer Priorität ausgewählt.|  
  
 Darüber hinaus wird die Standardauswahl für einen Editor des aktuellen Benutzers in HKEY\_Current\_User\\Software\\Microsoft\\VisualStudio\\ gespeichert*X.Y*\\Default Editors\\*Ext*. Die GUID des Sprachdiensts ausgewählten wird der benutzerdefinierte Eintrag. Dadurch wird für den aktuellen Benutzer.  
  
### Beispiel  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      Extensions\  
       (Default) = reg_sz:  
       *         = reg_dword:0x00000018  
       html      = reg_dword:0x00000027  
       shtm      = reg_dword:0x00000027  
       shtml     = reg_dword:0x00000027  
```  
  
## Registrierungseinträge für verwaltete Paket Framework Language Service\-Optionen  
 Die folgenden Registrierungseinträge sind spezifisch für die verwalteten Paket Framework \(MPF\) Sprache Dienstklassen. Diese Registrierungseinträge werden Unterstützung in der Sprachdienst für verschiedene IntelliSense\-Funktionen und andere erweiterte Bearbeitungsfunktionen angeben.  
  
 Diese Registrierungseinträge erfolgt über die <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse.  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|---------|-------------|------------------|  
|CodeSense|REG\_DWORD|0\-1|Unterstützung für IntelliSense\-Vorgänge.|  
|MatchBraces|REG\_DWORD|0\-1|Unterstützung für Paaren Sprache wie z. B. geschweifte Klammern, Klammern und Klammern.|  
|QuickInfo|REG\_DWORD|0\-1|Unterstützung für die IntelliSense\-QuickInfo\-Vorgang.|  
|ShowMatchingBrace|REG\_DWORD|0\-1|Unterstützung für die entsprechende Sprachpaar in der Statusleiste anzeigen.|  
|MatchBracesAtCaret|REG\_DWORD|0\-1|Unterstützung für die Anzeige von Language\-Paare in der Regel durch die beiden Elemente hervorheben.|  
|MaxErrorMessages|REG\_DWORD|0\-n|Die maximale Anzahl von Fehlern, die in angezeigt werden, die **Fehlerliste** Fenster.|  
|CodeSenseDelay|REG\_DWORD|0\-n|Die Anzahl der Millisekunden für die Verzögerung der Analyse für einen IntelliSense\-Vorgang im Hintergrund initiiert.|  
|EnableAsyncCompletion|REG\_DWORD|0\-1|Unterstützung für das Analysieren im Hintergrund.|  
|EnableCommenting|REG\_DWORD|0\-1|Unterstützung für ausgewählte Textblöcke auskommentieren und darüber hinaus Unterstützung für dabei markierten Text angegeben.|  
|EnableFormatSelection|REG\_DWORD|0\-1|Unterstützung für das Formatieren von Text, z. B. automatische Einzug oder Anpassen der Position der Klammern.|  
|AutoOutlining|REG\_DWORD|0\-1|Unterstützung für eine Gliederung \(Bereiche, die reduziert werden können\).|  
|MaxRegions|REG\_DWORD|0\-n|Die maximale Anzahl der ausgeblendeten Bereiche pro Datei.|  
  
```  
ExampleHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      XML\  
        (Default)             = reg_sz:{f6819a78-a205-47b5-be1c-675b3c7f0b8e}  
        MatchBraces           = reg_dword:0x00000001  
        QuickInfo             = reg_dword:0x00000001  
        ShowMatchingBrace     = reg_dword:0x00000001  
        MatchBracesAtCaret    = reg_dword:0x00000000  
        MaxErrorMessages      = reg_dword:0x00000064  
        CodeSenseDelay        = reg_dword:0x000001f4  
        MaxRegions            = reg_dword:0x0000000a  
```  
  
## Siehe auch  
 [Entwickeln einer Sprache](../../extensibility/internals/developing-a-legacy-language-service.md)