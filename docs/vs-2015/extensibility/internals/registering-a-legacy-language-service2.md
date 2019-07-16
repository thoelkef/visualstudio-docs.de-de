---
title: Registrieren von einem Legacysprachdienst 2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 07d70bb1d77dc3022b06c4036317e31692307f98
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188838"
---
# <a name="registering-a-legacy-language-service"></a>Registrieren eines Legacysprachdiensts
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die folgenden Abschnitte enthalten Listen der Registrierungseinträge für die verschiedenen Sprach Dienstoptionen verfügbaren in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 In der folgenden Liste der Registrierungseinträge *Stamm der VS-Reg* gleich HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, wobei *X.Y* ist die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Versionsnummer.  
  
## <a name="registry-entries-for-language-service-options"></a>Registrierungseinträge für den Dienst der Sprachoptionen  
 Die *Stamm der VS-Reg*\Languages\Language Services\\*Sprachenname* Schlüssel kann die folgenden Werte enthalten.  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|----------|-----------|-----------------|  
|(Standard)|REG_SZ|*\<GUID>*|Die GUID des Sprachdiensts.|  
|LangResID|REG_DWORD|0 x 0 – 0xffff|Ressourcenbezeichner ("RESID") für den Namen lokalisierter Text, der die Sprache eine Zeichenfolge.|  
|Package|REG_SZ|*\<GUID>*|Die GUID des VSPackage.|  
|ShowCompletion|REG_DWORD|0-1|Gibt an, ob die **Anweisungsvervollständigung** "Optionen" der **Optionen** Dialogfeld aktiviert sind.|  
|ShowSmartIndent|REG_DWORD|0-1|Gibt an, ob die Option zum auswählen **intelligente** Einzug der **Optionen** Dialogfeld ist aktiviert.|  
|RequestStockColors|REG_DWORD|0-1|Gibt an, ob der benutzerdefinierten oder standardmäßigen Farben werden verwendet, um die Farbe, die Schlüsselwörter.|  
|ShowHotURLs|REG_DWORD|0-1|Gibt an, ob der Benutzer auf URLs klicken kann.|  
|Standardmäßig nicht Hot-URLs|REG_DWORD|0-1|Gibt an, die ursprüngliche Einstellung für die **einfaches Klicken für URLs aktivieren** option die **Optionen** Dialogfeld.|  
|DefaultToInsertSpaces|REG_DWORD|0-1|Gibt an, ob der Sprachdienst "Leerzeichen einfügen" als die Standardoption für die Registerkarte ist.|  
|ShowDropdownBarOption|REG_DWORD|0-1|Aktiviert oder deaktiviert die **Navigationsleiste** option die **Optionen** Dialogfeld, das Anzeigen oder Ausblenden der **Navigationsleiste**.|  
|Nur die einzelnen Code-Fenster|REG_DWORD|0-1|Aktiviert oder deaktiviert die **neues Fenster** Choice in die **Fenster** Menü für einen Sprachdienst.|  
|EnableAdvancedMembersOption|REG_DWORD|0-1|Aktiviert oder deaktiviert ein **Optionen** Einstellung der im Dialogfeld für **Erweiterte Member ausblenden**.|  
|Das CF_HTML-Unterstützung|REG_DWORD|0-1|Gibt an, ob der Editor ermöglicht, kopieren und Einfügen von HTML-Daten.|  
|EnableLineNumbersOption|REG_DWORD|0-1|Gibt an, ob die **Zeilennummern** "Optionen" der **Optionen** im Dialogfeld für einen Sprachdienst aktiviert ist.|  
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Gibt an, ob erweiterte Member wie z. B. private Felder in Vervollständigungslisten ausgeblendet werden.|  
|ShowBraceCompletion|REG_DWORD|0-1|Gibt an, ob die **Abschluss in geschweifte Klammern eingeschlossen** option die **Optionen** Dialogfeld ist aktiviert.|  
  
### <a name="example"></a>Beispiel  
  
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
  
## <a name="registry-entries-for-debugger-languages-options"></a>Registrierungseinträge für Sprachen von Debuggeroptionen  
 Die *Stamm der VS-Reg*\Languages\Language Services\\*Sprachenname*\Debugger Sprachen\\*GUID*\ Schlüssel kann Folgendes beinhalten Werte.  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|----------|-----------|-----------------|  
|(Standard)|REG_SZ|Text|Der Standardwert kann verwendet werden, um den Namen der Sprache zu dokumentieren. Der Name dieses Schlüssels ist eine GUID eines ausdrucksauswerters, die einen entsprechenden Eintrag in  *\<VS Reg-Stamm >* \AD7Metrics\Expression Ausdrucksauswertung.|  
  
### <a name="example"></a>Beispiel  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        Debugger Languages\  
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\  
            (Default) = reg_sz:C++  
```  
  
## <a name="registry-entries-for-editor-tools-options"></a>Registrierungseinträge für Editor-Tools-Optionen  
 Sie können Registrierungsschlüssel unter dem Schlüssel EditorToolsOptions für Eigenschaftenseiten und die Eigenschaftsknoten hinzufügen. Diese Schlüssel und deren Werte identifizieren Sie die Eigenschaftenseiten in der **Optionen** Dialogfeld (auf der **Tools** Menü), werden verwendet, um den Sprachdienst zu konfigurieren. Im folgenden Beispiel *Seitennamen* ist der Name der auf einer Eigenschaftenseite und *Knotenname* befindet sich auf der Namen eines Knotens in der Struktur der **Optionen** Dialogfeld. Die seiteneintrag und die Knoten-Eintrag müssen separat angegeben werden.  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|----------|-----------|-----------------|  
|(Standard)|REG_SZ|"RESID"|Der lokalisierte Anzeigename von dieser Seite. Der Name kann es sich um Literaltext oder #`nnn`, wobei `nnn` ist eine Zeichenfolge-Ressourcen-ID in der Satelliten-DLL des angegebenen VSPackage.|  
|Package|REG_SZ|*GUID*|Die GUID des VSPackage, das diese Optionsseite implementiert.|  
|Seite|REG_SZ|*GUID*|Die GUID des auf der Seite der Anforderung aus dem VSPackage durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> Methode. Wenn dieser Registrierungseintrag nicht vorhanden ist, wird der Registrierungsschlüssel einen Knoten, die nicht auf einer Seite beschrieben.|  
  
### <a name="example"></a>Beispiel  
  
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
  
## <a name="registry-entries-for-file-name-extension-options"></a>Registrierungseinträge für die Optionen für Namen Dateierweiterung  
 Der Eintrag für die Erweiterung sollte es sich um den Punkt, z. B. ".myext" enthalten.  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|----------|-----------|-----------------|  
|(Standard)|REG_SZ|*GUID*|Dienst-GUID für den Standard-Sprachdienst für diesen Dateityp des Name-Erweiterung.|  
  
### <a name="example"></a>Beispiel  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    File Extensions\  
      .cpp\  
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
```  
  
## <a name="registry-entries-for-editor-options"></a>Registrierungseinträge für Editor-Optionen  
 Die *Stamm der VS-Reg*\Editors-Schlüssel kann die folgenden Werte enthalten:  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|----------|-----------|-----------------|  
|(Standard)|REG_SZ|""|Nicht verwendet; Sie können Ihren Namen für die Dokumentation hier einfügen.|  
|DefaultToolboxTab|REG_SZ|""|Name der Toolboxregisterkarte, der als Standard festlegen, wenn der Editor aktiv ist.|  
|DisplayName|REG_SZ|"RESID"|Anzuzeigenden Namen der **Öffnen mit** Dialogfeld. Der Name ist die Zeichenfolgenressource-ID oder ein Name im Standardformat.|  
|ExcludeDefTextEditor|REG_DWORD|0-1|Verwendet für die **Öffnen mit** Menübefehl. Wenn Sie nicht die Standard-Text-Editor in der Liste der verfügbaren Editoren anzuzeigen, für einen bestimmten Dateityp auflisten möchten, legen Sie diesen Wert auf 1 fest.|  
|LinkedEditorGUID|REG_SZ|*\<GUID>*|Verwendet für alle Sprachdienst, der eine Datei mit der Codepage-Unterstützung öffnen kann. Z. B. beim Öffnen einer TXT-Datei mithilfe der **Öffnen mit** Befehl Optionen stehen zur Verfügung, für die Verwendung der Quellcode-Editor, mit und ohne Codierung.<br /><br /> Die GUID, die Namen der Unterschlüssel angegeben ist, für die Codepage-Editor-Factory. in diesem bestimmten Registrierungseintrag angegebene verknüpfte GUID ist für die reguläre Editor-Factory. Der Zweck dieses Eintrags ist, wenn die IDE keine Datei mit dem Standardeditor öffnen, die IDE versucht, den nächsten Editor in der Liste verwenden. Dieser nächste Editor darf nicht die Codepage-Editor-Factory sein, da dieser Editorfactory im Grunde die Editor-Factory identisch ist, die Fehler.|  
|Package|REG_SZ|*\<GUID>*|VSPackage GUID für den Anzeigenamen "RESID".|  
  
### <a name="example"></a>Beispiel  
  
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
  
## <a name="registry-entries-for-logical-view-options"></a>Registrierungseinträge für die logische Ansicht-Optionen  
 Die *Stamm der VS-Reg*\Editors\\ *-Editor-GUI >* \LogicalViews-Schlüssel kann die folgenden Werte enthalten.  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|----------|-----------|-----------------|  
|(Standard)|REG_SZ||Nicht verwendet.|  
|*\<GUID>*|REG_SZ|""|Schlüssel, der die unterstützten logischen Ansichten. Sie können beliebig viele verwenden, wie Sie benötigen. Der Name des Registrierungseintrags ist von Bedeutung, nicht den Wert, der immer eine leere Zeichenfolge ist.|  
  
### <a name="example"></a>Beispiel  
  
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
  
## <a name="registry-entries-for-editor-extension-options"></a>Registrierungseinträge für die Erweiterung des Editors-Optionen  
 Die *Stamm der VS-Reg*\Editors\\*Editor GUID*\Extensions-Schlüssel kann die folgenden Werte enthalten. Die Dateinamenerweiterung ist nicht mit der führenden Punkt enthalten.  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|----------|-----------|-----------------|  
|(Standard)|REG_SZ||Nicht verwendet.|  
|*\<Ext >*|REG_DWORD|0-0xffffffff|Relative Priorität von Erweiterungen. Wenn zwei oder mehr Sprachen die gleiche Erweiterung verwenden, wird die Sprache der höheren Priorität ausgewählt.|  
  
 Darüber hinaus befindet sich der aktuelle Benutzer die Standardauswahl für einen Editor in HKEY_Current_User\Software\Microsoft\VisualStudio\\*X.Y*\Default Editoren\\*Ext*. Die GUID des Sprachdiensts ausgewählten ist im Custom-Eintrag. Dies hat es sich um Vorrang vor, für den aktuellen Benutzer.  
  
### <a name="example"></a>Beispiel  
  
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
  
## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Registrierungseinträge für Managed Package Framework-Sprache-Service-Optionen  
 Die folgenden Registrierungseinträge sind spezifisch für die verwaltete Package Framework (MPF) Sprache-Dienstklassen. Diese Registrierungseinträge angeben-Unterstützung in den Sprachdienst für verschiedene IntelliSense-Funktionen und andere erweiterte Bearbeitungsfunktionen.  
  
 Diese Registrierungseinträge erfolgt über die <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse.  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|----------|-----------|-----------------|  
|CodeSense|REG_DWORD|0-1|Unterstützung für IntelliSense-Vorgänge.|  
|MatchBraces|REG_DWORD|0-1|Unterstützung für die entsprechende Sprachpaare z. B. von geschweiften Klammern und runde sowie eckige Klammern.|  
|QuickInfo|REG_DWORD|0-1|Unterstützung für den IntelliSense-QuickInfo-Vorgang.|  
|ShowMatchingBrace|REG_DWORD|0-1|Unterstützung für das entsprechende Sprachpaar in der Statusleiste angezeigt.|  
|MatchBracesAtCaret|REG_DWORD|0-1|Unterstützung für die Anzeige von entsprechende Sprachpaare, in der Regel durch die zwei Elemente markieren.|  
|MaxErrorMessages|REG_DWORD|0-n-Gerät|Die maximale Anzahl von Fehlern, die in angezeigt werden, kann die **Fehlerliste** Fenster.|  
|CodeSenseDelay|REG_DWORD|0-n-Gerät|Die Anzahl der Millisekunden, um vor dem Initiieren des Analysieren von ASP.NET-Vorlagen für einen IntelliSense-Vorgang im Hintergrund verzögert.|  
|EnableAsyncCompletion|REG_DWORD|0-1|Unterstützung für das Analysieren im Hintergrund.|  
|EnableCommenting|REG_DWORD|0-1|Unterstützung für die ausgewählte Textblöcke auskommentieren und auch Unterstützung für die Kommentierung Textauswahl impliziert.|  
|EnableFormatSelection|REG_DWORD|0-1|Unterstützung für die Formatierung von Text wie z. B. automatischer-Einzug, oder die Position geschweifter Klammern anpassen.|  
|AutoOutlining|REG_DWORD|0-1|Unterstützung für eine Gliederung (Bereiche, die reduziert werden können).|  
|MaxRegions|REG_DWORD|0-n-Gerät|Die maximale Anzahl der ausgeblendeten Bereiche pro Datei.|  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln eines Legacysprachdiensts](../../extensibility/internals/developing-a-legacy-language-service.md)
