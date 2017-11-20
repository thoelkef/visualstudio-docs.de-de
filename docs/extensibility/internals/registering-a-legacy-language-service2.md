---
title: "Registrieren eine Vorgängerversion Sprache Service2 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f64b02521fcea9abef9d7196a27e4a209100a892
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="registering-a-legacy-language-service"></a>Registrieren einen Sprachdienst Legacy
Die folgenden Abschnitte enthalten Listen von Registrierungseinträgen für die verschiedenen Sprache Dienstoptionen verfügbaren in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 In der folgenden Liste von Registrierungseinträgen *VS Reg Stamm* gleich HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, wobei *X.Y* ist die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Versionsnummer.  
  
## <a name="registry-entries-for-language-service-options"></a>Registrierungseinträge für den Dienst Sprachoptionen  
 Die *VS Reg Stamm*\Languages\Language Services\\*Sprachenname* Schlüssel kann die folgenden Werte enthalten.  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|----------|-----------|-----------------|  
|(Standard)|REG_SZ|*\<GUID >*|Die GUID des Sprachdiensts.|  
|LangResID|REG_DWORD|0 x 0 – 0xffff|Zeichenfolge Ressourcenbezeichner (ResID) für den lokalisierten Textnamen der Sprache an.|  
|Package|REG_SZ|*\<GUID >*|Die GUID des VSPackage.|  
|ShowCompletion|REG_DWORD|0-1|Gibt an, ob die **Anweisungsvervollständigung** Optionen in der **Optionen** Dialogfeld aktiviert sind.|  
|ShowSmartIndent|REG_DWORD|0-1|Gibt an, ob die Option zur Auswahl **Smart** den Einzug den **Optionen** Dialogfeld aktiviert ist.|  
|RequestStockColors|REG_DWORD|0-1|Gibt an, ob benutzerdefinierte oder Standardfarben werden verwendet, um die Farbe der Schlüsselwörter.|  
|ShowHotURLs|REG_DWORD|0-1|Gibt an, ob der Benutzer, URLs klicken kann.|  
|Standardmäßig nicht im laufenden Systembetrieb URLs|REG_DWORD|0-1|Gibt an, die ursprüngliche Einstellung für die **einfaches Klicken für URLs aktivieren** -Option in der **Optionen** (Dialogfeld).|  
|DefaultToInsertSpaces|REG_DWORD|0-1|Gibt an, ob der Sprachdienst verfügt "Leerzeichen einfügen" als die Standardoption für die Registerkarte ".|  
|ShowDropdownBarOption|REG_DWORD|0-1|Aktiviert oder deaktiviert die **Navigationsleiste** -Option in der **Optionen** (Dialogfeld), die zeigt, oder blendet Sie aus der **Navigationsleiste**.|  
|Nur einzelne Codefenster|REG_DWORD|0-1|Aktiviert oder deaktiviert die **neues Fenster** Auswahlen in den **Fenster** Menü für einen Sprachdienst.|  
|EnableAdvancedMembersOption|REG_DWORD|0-1|Aktiviert oder deaktiviert eine **Optionen** Einstellung der im Dialogfeld für **Erweiterte Member ausblenden**.|  
|Unterstützung CF_HTML|REG_DWORD|0-1|Gibt an, ob der Editor ermöglicht, kopieren und Einfügen von HTML-Daten.|  
|EnableLineNumbersOption|REG_DWORD|0-1|Gibt an, ob die **Zeilennummern** Optionen in der **Optionen** im Dialogfeld für einen Sprachdienst aktiviert ist.|  
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Gibt an, ob erweiterte Member, z. B. private Felder in Vervollständigungslisten ausgeblendet sind.|  
|ShowBraceCompletion|REG_DWORD|0-1|Gibt an, ob die **Abschluss in geschweifte Klammern eingeschlossen** -Option in der **Optionen** Dialogfeld aktiviert ist.|  
  
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
  
## <a name="registry-entries-for-debugger-languages-options"></a>Registrierungseinträge für Sprachen Debuggeroptionen  
 Die *VS Reg Stamm*\Languages\Language Services\\*Sprachenname*\Debugger Sprachen\\*GUID*\ Schlüssel kann Folgendes enthalten Werte.  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|----------|-----------|-----------------|  
|(Standard)|REG_SZ|Text|Der Standardwert kann verwendet werden, um den Namen der Sprache zu dokumentieren. Der Name der dieser Schlüssel ist eine GUID, der eine ausdrucksauswertung, der einen entsprechenden Eintrag in  *\<VS Reg-Stamm >*\AD7Metrics\Expression bei der Ausdrucksauswertung.|  
  
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
  
## <a name="registry-entries-for-editor-tools-options"></a>Registrierungseinträge für Editor-Menü Extras, Optionen  
 Sie können Registrierungsschlüssel unter dem Schlüssel EditorToolsOptions für Eigenschaftenseiten und Eigenschaftsknoten hinzufügen. Diese Schlüssel und deren Werte identifizieren Eigenschaftenseiten in der **Optionen** (Dialogfeld) (auf der **Tools** Menü) zum Konfigurieren des Sprachdiensts verwendet werden. Im folgenden Beispiel *Seitennamen* ist der Name einer Eigenschaftenseite und *Knotenname* befindet sich auf der Namen eines Knotens in der Struktur der **Optionen** (Dialogfeld). Der Eintrag für die Seite und die Knoten-Eintrag müssen separat angegeben werden.  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|----------|-----------|-----------------|  
|(Standard)|REG_SZ|resID|Der lokalisierte Name der diese Optionsseite. Der Name kann Literaltext oder #`nnn`, wobei `nnn` ist eine Zeichenfolge-Ressourcen-ID in der Satelliten-DLL des angegebenen VSPackage.|  
|Package|REG_SZ|*GUID*|Die GUID des VSPackage, das diese Optionsseite implementiert.|  
|Seite|REG_SZ|*GUID*|Die GUID der Eigenschaftenseite aus dem VSPackage anfordern, durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> Methode. Wenn dieses Registrierungseintrags nicht vorhanden ist, wird der Registrierungsschlüssel einen Knoten, die nicht auf einer Seite beschrieben.|  
  
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
  
## <a name="registry-entries-for-file-name-extension-options"></a>Registrierungseinträge für Dateinamenoptionen-Erweiterung  
 Der Eintrag für die Erweiterung sollte den führenden Punkt, z. B. ".myext" enthalten.  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|----------|-----------|-----------------|  
|(Standard)|REG_SZ|*GUID*|Dienst-GUID für die Language-Standarddienst für diesen Dateityp für Name-Erweiterung.|  
  
### <a name="example"></a>Beispiel  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    File Extensions\  
      .cpp\  
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
```  
  
## <a name="registry-entries-for-editor-options"></a>Registrierungseinträge für Editor-Optionen  
 Die *VS Reg Stamm*\Editors Schlüssel kann die folgenden Werte enthalten:  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|----------|-----------|-----------------|  
|(Standard)|REG_SZ|""|Nicht verwendete; Sie können Ihre Namen Dokumentation hier einfügen.|  
|DefaultToolboxTab|REG_SZ|""|Der Name der Toolbox-Registerkarte Standard, die bei der Editor aktiv ist.|  
|DisplayName|REG_SZ|resID|Name, der in der **Öffnen mit** (Dialogfeld). Der Name ist die Zeichenfolgenressource-ID oder einen Namen im Standardformat.|  
|ExcludeDefTextEditor|REG_DWORD|0-1|Verwendet für die **Öffnen mit** Menübefehl. Wenn Sie nicht die Standard-Text-Editor in der Liste der verfügbaren Editoren für einen bestimmten Dateityp auflisten möchten, legen Sie diesen Wert auf 1 fest.|  
|LinkedEditorGUID|REG_SZ|*\<GUID >*|Verwendet für alle Sprachdienst, die eine Datei mit Unterstützung für Codepage öffnen können. Z. B. beim Öffnen einer TXT-Datei mithilfe der **Öffnen mit** Befehl Optionen stehen zur Verfügung, für die Verwendung der Quellcode-Editors mit und ohne Codierung.<br /><br /> Die GUID, die Namen der Unterschlüssel angegeben ist, für die Codepage-Editor-Factory. in diesem bestimmten Registrierungseintrag angegebene verknüpfte GUID ist für die reguläre Editorfactory. Der Zweck dieses Eintrags ist, wenn die IDE keine Datei mit dem Standardeditor öffnen, die IDE versucht, den nächsten-Editor in der Liste zu verwenden. Dieser weiter Editor darf nicht der Codepage-Editor-Factory sein, da dieser Editorfactory im Grunde als die Editor-Factory ist, die Fehler.|  
|Package|REG_SZ|*\<GUID >*|VSPackage-GUID für den Anzeigenamen ResID.|  
  
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
  
## <a name="registry-entries-for-logical-view-options"></a>Registrierungseinträge für logische Ansichtsoptionen  
 Die *VS Reg Stamm*\Editors\\*GUI-Editor >*\LogicalViews Schlüssel kann die folgenden Werte enthalten.  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|----------|-----------|-----------------|  
|(Standard)|REG_SZ||Nicht verwendet.|  
|*\<GUID >*|REG_SZ|""|Der Schlüssel, die den logischen Ansichten unterstützt. Sie können beliebig viele davon haben, wie Sie benötigen. Der Name des Registrierungseintrags ist von Bedeutung, nicht den Wert, der immer eine leere Zeichenfolge ist.|  
  
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
  
## <a name="registry-entries-for-editor-extension-options"></a>Registrierungseinträge für Editor-Erweiterung  
 Die *VS Reg Stamm*\Editors\\*-Editor-GUID*\Extensions Schlüssel kann die folgenden Werte enthalten. Die Dateinamenerweiterung umfasst nicht die führenden Punkt.  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|----------|-----------|-----------------|  
|(Standard)|REG_SZ||Nicht verwendet.|  
|*\<Ext >*|REG_DWORD|0-0xffffffff|Relative Priorität der Erweiterungen. Wenn zwei oder mehrere Sprachen gemeinsam die gleiche Erweiterung verwendet haben, wird die Sprache höherer Priorität ausgewählt.|  
  
 Darüber hinaus wird die Standardauswahl für einen Editor des aktuellen Benutzers in HKEY_Current_User\Software\Microsoft\VisualStudio gespeichert\\*X.Y*\Default Editoren\\*Ext*. Die GUID des Sprachdiensts ausgewählten wird der benutzerdefinierte Eintrag. Dies Vorrang für den aktuellen Benutzer.  
  
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
  
## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Registrierungseinträge für Managed Package Framework Service Sprachoptionen  
 Die folgenden Registrierungseinträge sind spezifisch für die verwaltete Package Framework (MPF) Sprache Dienstklassen. Diese Registrierungseinträge werden Unterstützung in der Sprachdienst für verschiedene IntelliSense-Funktionen und andere erweiterte Bearbeitungsfunktionen angeben.  
  
 Diese Registrierungseinträge erfolgt über die <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse.  
  
|Name|Typ|Bereich|Beschreibung|  
|----------|----------|-----------|-----------------|  
|CodeSense|REG_DWORD|0-1|Unterstützung für IntelliSense-Vorgänge.|  
|MatchBraces|REG_DWORD|0-1|Unterstützung für den Abgleich von Sprache-ersetzungswertpaaren, z. B. geschweifte Klammern, runden und eckigen Klammern.|  
|QuickInfo|REG_DWORD|0-1|Unterstützung für die IntelliSense-QuickInfo-Vorgang.|  
|ShowMatchingBrace|REG_DWORD|0-1|Unterstützung für die entsprechende Sprachpaar anzeigt, in der Statusleiste.|  
|MatchBracesAtCaret|REG_DWORD|0-1|Unterstützung für die Anzeige von übereinstimmende Sprachpaare, in der Regel durch das Hervorheben von zwei Elementen.|  
|MaxErrorMessages|REG_DWORD|0-n|Die maximale Anzahl von Fehlern, die in angezeigt werden, die **Fehlerliste** Fenster.|  
|CodeSenseDelay|REG_DWORD|0-n|Die Anzahl der Millisekunden, die Verzögerung, bevor die Analyse für einen IntelliSense-Vorgang im Hintergrund initiiert.|  
|EnableAsyncCompletion|REG_DWORD|0-1|Unterstützung für das Analysieren im Hintergrund.|  
|EnableCommenting|REG_DWORD|0-1|Unterstützung für die ausgewählte Textblöcke auskommentieren, und darüber hinaus Unterstützung für uncommenting markierten Text angegeben.|  
|EnableFormatSelection|REG_DWORD|0-1|Unterstützung für das Formatieren von Text, z. B. automatische Einzug, oder passen Sie die Position geschweifter Klammern.|  
|AutoOutlining|REG_DWORD|0-1|Unterstützung für eine Gliederung (Regionen, die reduziert werden können).|  
|MaxRegions|REG_DWORD|0-n|Die maximale Anzahl der ausgeblendete Bereiche pro Datei.|  
  
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