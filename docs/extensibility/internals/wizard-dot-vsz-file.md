---
title: Wizard (. Vsz) Datei | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0fedf409c0ca320c054ddf1cc16318d08d25463a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703307"
---
# <a name="wizard-vsz-file"></a>Assistentendatei (VSZ)

Die integrierte Entwicklungsumgebung (IDE) verwendet .vsz-Dateien, um Assistenten zu starten. Diese .vsz-Dateien enthalten Informationen, die die IDE verwendet, um zu bestimmen, welcher Assistent aufruft und welche Informationen an den Assistenten übergeben werden sollen.

Eine .vsz-Datei ist eine Version einer .ini-formatierten Textdatei, die keine Abschnitte enthält. Die der IDE bekannten Informationen werden am Anfang der Datei gespeichert. Dadurch wird eine Verknüpfung zwischen dem Assistenten, den die IDE aufruft, und den Parametern in der .vsz-Datei hergestellt, die an die IDE übergeben werden soll. Der Rest der Datei enthält Parameter, die für den Assistenten spezifisch sind und von der IDE gesammelt und an den jeweiligen Assistenten übergeben werden sollen.

Das folgende Beispiel zeigt den Inhalt einer .vsz-Datei.

```
VSWizard 8.0
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}
Param="WIZARDNAME = Wizard One"
Param="WIZARDUI = FALSE"
```

Im Folgenden sind die Teile in der .vsz-Datei zu finden.

|Teil|BESCHREIBUNG|
|----------|-----------------|
|Vswizard|Der erste Parameter in der Datei ist die Versionsnummer des Vorlagendateiformats. Diese Versionsnummer muss 6.0, 7.0, 7.1 oder 8.0 sein. Andere Zahlen können nicht gestartet werden und verursachen einen Fehler im ungültigen Format.|
|Assistent|Dieses Feld enthält die OLE-ProgID des Assistenten oder alternativ eine GUID-Zeichenfolgendarstellung der CLSID des Assistenten, die von der IDE gemeinsam erstellt wird.|
|Parameter|Diese Teile sind optional. Sie können benötigst viele hinzufügen.|

Die Parameter ermöglichen es der .vsz-Datei, zusätzliche benutzerdefinierte Parameter an den Assistenten zu übergeben. Jeder Wert wird als Zeichenfolgenelement in einem Array von Varianten an den Assistenten übergeben. Weitere Informationen finden Sie unter [Benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md).

Um Ihrer .vsz-Datei eine Standardgebietsschema-ID hinzuzufügen, geben Sie `FALLBACK_LCID`=xxxx an, wobei xxxx die Gebietsschema-ID ist, z. B. 1033 für Englisch. Wenn `FALLBACK_LCID` der Parameter definiert ist, verwendet der Assistent die angegebene Fallbackgebietsschema-ID, wenn die aktuelle ID nicht gefunden wird.

## <a name="see-also"></a>Weitere Informationen

- [Benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md)
- [Assistenten](../../extensibility/internals/wizards.md)
- [Dateien zur Beschreibung des Vorlagenverzeichnisses (VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
