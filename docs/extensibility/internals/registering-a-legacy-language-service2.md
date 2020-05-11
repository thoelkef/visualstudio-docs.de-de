---
title: Registrieren eines Legacy Language Service2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d9d13f301f6c04c0f7b14cc8c685f08b072ef84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705884"
---
# <a name="registering-a-legacy-language-service"></a>Registrieren eines Legacysprachdiensts
In den folgenden Abschnitten finden Sie Listen mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Registrierungseinträgen für die verschiedenen Sprachdienstoptionen, die in verfügbar sind.

 In der folgenden Liste der Registrierungseinträge ist *VS Reg Root* gleich\\HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] *X.Y*, wobei *X.Y* die Versionsnummer ist.

## <a name="registry-entries-for-language-service-options"></a>Registrierungseinträge für Sprachdienstoptionen
 Der Sprachnamen *VS Reg*\\Root ,Sprachen,*Sprachdienste,* kann die folgenden Werte enthalten.

|Name|type|Bereich|BESCHREIBUNG|
|----------|----------|-----------|-----------------|
|(Standardwert)|REG_SZ|*\<GUID->*|GUID des Sprachdienstes.|
|LangResID|REG_DWORD|0x0-0xffff|String-Ressourcenbezeichner (ResID) für den lokalisierten Textnamen der Sprache.|
|Paket|REG_SZ|*\<GUID->*|GUID des VSPackage.|
|ShowCompletion|REG_DWORD|0-1|Gibt an, ob die **Anweisungsvervollständigungsoptionen** im Dialogfeld **Optionen** aktiviert sind.|
|ShowSmartIndent|REG_DWORD|0-1|Gibt an, ob die Option zur Auswahl der Smart-Einrückung im Dialogfeld **Optionen** aktiviert ist. **Smart**|
|RequestStockColors|REG_DWORD|0-1|Gibt an, ob benutzerdefinierte oder Standardfarben zum Farbieren von Schlüsselwörtern verwendet werden.|
|ShowHotURLs|REG_DWORD|0-1|Gibt an, ob der Benutzer auf URLs klicken kann.|
|Standard wert auf Nicht-Hot-URLs|REG_DWORD|0-1|Gibt die Anfangseinstellung für die **URL-Navigationsoption** aktivieren im Dialogfeld **Optionen** an.|
|DefaultToInsertSpaces|REG_DWORD|0-1|Gibt an, ob der Sprachdienst über "Insert Spaces" als Standard-Registerkartenoption verfügt.|
|ShowDropdownBarOption|REG_DWORD|0-1|Aktiviert oder deaktiviert die **Navigationsleiste** im Dialogfeld **Optionen,** die die **Navigationsleiste**ein- oder ausblendet.|
|Nur Einzelcodefenster|REG_DWORD|0-1|Aktiviert oder deaktiviert die Option **"Neues Fenster"** im **Menü Fenster** für einen Sprachdienst.|
|EnableAdvancedMembersOption|REG_DWORD|0-1|Aktiviert oder deaktiviert **eine** Optionsdialogfeldeinstellung für **Erweiterte Mitglieder ausblenden**.|
|Unterstützung CF_HTML|REG_DWORD|0-1|Gibt an, ob der Editor das Kopieren und Einfügen von HTML-Daten aktiviert.|
|EnableLineNumbersOption|REG_DWORD|0-1|Gibt an, ob die **Liniennummernoptionen** im Dialogfeld **Optionen** für einen Sprachdienst aktiviert sind.|
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Gibt an, ob erweiterte Member, z. B. private Felder, in Abschlusslisten ausgeblendet sind.|
|ShowBraceCompletion|REG_DWORD|0-1|Gibt an, ob die Option **"Vervollständigung der Geschfürtung"** im Dialogfeld **Optionen** aktiviert ist.|

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

## <a name="registry-entries-for-debugger-languages-options"></a>Registrierungseinträge für Debugger languages-Optionen
 Der Sprachschlüssel *"VS Reg Root" (Sprachen)*\\und "Language Services Language*Name"* und "Debugger languages\\*GUID"* können die folgenden Werte enthalten.

|Name|type|Bereich|BESCHREIBUNG|
|----------|----------|-----------|-----------------|
|(Standardwert)|REG_SZ|text|Der Standardwert kann verwendet werden, um den Namen der Sprache zu dokumentieren. Der Name dieses Schlüssels ist eine GUID eines Ausdrucksevaluators, der einen entsprechenden Eintrag in * \<VS Reg Root>*.AD7Metrics-Expression Evaluator hat.|

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

## <a name="registry-entries-for-editor-tools-options"></a>Registrierungseinträge für Editor Tools-Optionen
 Sie können Registrierungsschlüssel unter dem EditorToolsOptions-Schlüssel für Eigenschaftenseiten und Eigenschaftsknoten hinzufügen. Diese Schlüssel und ihre Werte identifizieren Eigenschaftenseiten im Dialogfeld **Optionen** (im Menü **Extras),** die zum Konfigurieren des Sprachdienstes verwendet werden. Im folgenden Beispiel ist *Seitenname* der Name einer Eigenschaftenseite, und *Knotenname* ist der Name eines Knotens in der Struktur im Dialogfeld **Optionen.** Der Seiteneintrag und der Knoteneintrag müssen separat angegeben werden.

|Name|type|Bereich|BESCHREIBUNG|
|----------|----------|-----------|-----------------|
|(Standardwert)|REG_SZ|Resid|Der lokalisierte Anzeigename dieser Optionsseite. Der Name kann Literaltext`nnn`sein, `nnn` oder , wobei es sich um eine Zeichenfolgenressourcen-ID in der Satelliten-DLL des angegebenen VSPackage handelt.|
|Paket|REG_SZ|*Guid*|Die GUID des VSPackage, das diese Optionsseite implementiert.|
|Seite|REG_SZ|*Guid*|Die GUID der Eigenschaftenseite, die vom VSPackage durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> Methode anzufordern werden soll. Wenn dieser Registrierungseintrag nicht vorhanden ist, beschreibt der Registrierungsschlüssel einen Knoten und keine Seite.|

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

## <a name="registry-entries-for-file-name-extension-options"></a>Registrierungseinträge für Dateinamenerweiterungsoptionen
 Der Eintrag für die Dateierweiterung sollte die führende Periode enthalten, zum Beispiel ".myext".

|Name|type|Bereich|BESCHREIBUNG|
|----------|----------|-----------|-----------------|
|(Standardwert)|REG_SZ|*Guid*|Dienst-GUID für den Standardsprachdienst für diesen Dateinamenerweiterungstyp.|

### <a name="example"></a>Beispiel

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    File Extensions\
      .cpp\
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
```

## <a name="registry-entries-for-editor-options"></a>Registrierungseinträge für Editoroptionen
 Der VS Reg Root-Editor-Schlüssel kann die folgenden Werte enthalten: *VS Reg Root*

|Name|type|Bereich|BESCHREIBUNG|
|----------|----------|-----------|-----------------|
|(Standardwert)|REG_SZ|""|Unbenutzt; Sie können Ihren Namen hier zur Dokumentation eingeben.|
|DefaultToolboxTab|REG_SZ|""|Name der Toolbox-Registerkarte, die Standardeinstellung erstellt werden soll, wenn der Editor aktiv ist.|
|DisplayName|REG_SZ|Resid|Name, der im Dialogfeld **Öffnen mit** angezeigt werden soll. Der Name ist die Zeichenfolgenressourcen-ID oder ein Name im Standardformat.|
|ExcludeDefTextEditor|REG_DWORD|0-1|Wird für den Menübefehl **"Öffnen mit"** verwendet. Wenn Sie den Standardtexteditor nicht in der Liste der verfügbaren Editoren für einen bestimmten Dateityp auflisten möchten, legen Sie diesen Wert auf 1 fest.|
|LinkedEditorGUID|REG_SZ|*\<GUID->*|Wird für jeden Sprachdienst verwendet, der eine Datei mit Codepage-Unterstützung öffnen kann. Wenn Sie beispielsweise eine .txt-Datei mit dem Befehl **"Mit öffnen"** öffnen öffnen, werden Optionen für die Verwendung des Quellcode-Editors mit und ohne Codierung bereitgestellt.<br /><br /> Die im Namen des Unterschlüssels angegebene GUID ist für die Codepage-Editorfactory. Die in diesem spezifischen Registrierungseintrag angegebene verknüpfte GUID ist für die reguläre Editorfactory. Der Zweck dieses Eintrags besteht darin, dass die IDE versucht, den nächsten Editor in der Liste zu verwenden, wenn die IDE keine Datei mit dem Standardeditor öffnet. Dieser nächste Editor sollte nicht die Codepage-Editor-Factory sein, da diese Editorfactory im Grunde die gleiche ist wie die Editorfactory, die fehlgeschlagen ist.|
|Paket|REG_SZ|*\<GUID->*|VSPackage GUID für die ResID des Anzeigenamens.|

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
 Die *VS-Reg-Root-Editor-Editor-GUI*\\ *>*-Taste "LogicalViews" können die folgenden Werte enthalten.

|Name|type|Bereich|BESCHREIBUNG|
|----------|----------|-----------|-----------------|
|(Standardwert)|REG_SZ||Nicht verwendet.|
|*\<GUID->*|REG_SZ|""|Schlüssel zu den unterstützten logischen Ansichten. Sie können so viele davon haben, wie Sie brauchen. Der Name des Registrierungseintrags ist wichtig, nicht der Wert, der immer eine leere Zeichenfolge ist.|

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

## <a name="registry-entries-for-editor-extension-options"></a>Registrierungseinträge für Editorerweiterungsoptionen
 Der Schlüssel VS\\Reg *Root*-Editors Editor*GUID*-Extensions- und -Erweiterungen-Taste kann die folgenden Werte enthalten. Die Dateinamenerweiterung enthält nicht den führenden Zeitraum.

|Name|type|Bereich|BESCHREIBUNG|
|----------|----------|-----------|-----------------|
|(Standardwert)|REG_SZ||Nicht verwendet.|
|*\<ext>*|REG_DWORD|0-0xffffffff|Relative Priorität von Erweiterungen. Wenn zwei oder mehr Sprachen dieselbe Erweiterung verwenden, wird die Sprache mit höherer Priorität gewählt.|

 Darüber hinaus wird die Standardauswahl des aktuellen Benutzers für einen Editor\\in HKEY_Current_User-Software-Microsoft-VisualStudio*X.Y-Standard-Editoren*\\*ext*gespeichert. Die GUID des ausgewählten Sprachdienstes befindet sich im benutzerdefinierten Eintrag. Dies hat für den aktuellen Benutzer Vorrang.

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

## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Registrierungseinträge für Managed Package Framework Language Service-Optionen
 Die folgenden Registrierungseinträge sind spezifisch für die MPF-Sprachdienstklassen (Managed Package Framework). Diese Registrierungseinträge zeigen die Unterstützung im Sprachdienst für verschiedene IntelliSense-Funktionen und für andere erweiterte Bearbeitungsfunktionen an.

 Auf diese Registrierungseinträge <xref:Microsoft.VisualStudio.Package.LanguagePreferences> wird über die Klasse zugegriffen.

|Name|type|Bereich|BESCHREIBUNG|
|----------|----------|-----------|-----------------|
|CodeSense|REG_DWORD|0-1|Unterstützung für IntelliSense-Vorgänge.|
|MatchBraces|REG_DWORD|0-1|Unterstützung für übereinstimmende Sprachpaare wie geschweifte Klammern, Klammern und Klammern.|
|QuickInfo|REG_DWORD|0-1|Unterstützung für den IntelliSense Quick Info-Vorgang.|
|ShowMatchingBrace|REG_DWORD|0-1|Unterstützung für die Anzeige des passenden Sprachpaars in der Statusleiste.|
|MatchBracesAtCaret|REG_DWORD|0-1|Unterstützung für die Anzeige übereinstimmender Sprachpaare, in der Regel durch Hervorheben der beiden Elemente.|
|MaxErrorMessages|REG_DWORD|0-n|Die maximale Anzahl von Fehlern, die im Fenster **Fehlerliste** angezeigt werden können.|
|CodeSenseDelay|REG_DWORD|0-n|Die Anzahl der Millisekunden, die verzögert werden müssen, bevor eine Hintergrundanalyse für einen IntelliSense-Vorgang ausgelöst wird.|
|EnableAsyncCompletion|REG_DWORD|0-1|Unterstützung für die Hintergrundanalyse.|
|EnableCommenting|REG_DWORD|0-1|Unterstützung für das Kommentieren ausgewählter Textblöcke und bedeutet auch Unterstützung für die Nichtkommendere ausgewählter Text.|
|EnableFormatSelection|REG_DWORD|0-1|Unterstützung für das Formatieren von Text, z. B. automatische eingerückt oder Anpassen der Position von geschweiften Klammern.|
|AutoOutlining|REG_DWORD|0-1|Unterstützung für die Gliederung (Regionen, die zusammengeklappt werden können).|
|MaxRegions|REG_DWORD|0-n|Die maximale Anzahl ausgeblendeter Bereiche pro Datei.|

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

## <a name="see-also"></a>Weitere Informationen
- [Entwickeln eines Legacysprachdiensts](../../extensibility/internals/developing-a-legacy-language-service.md)
