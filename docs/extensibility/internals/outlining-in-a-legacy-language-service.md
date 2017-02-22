---
title: "Gliederung im ein Legacy-Sprachdienst | Microsoft Docs"
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
  - "Gliedern"
  - "Gliederung Sprachdienste [Verwaltetes Paketframework]"
  - "Gliedern, Unterstützung in Sprachdienste [Verwaltetes Paketframework]"
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Gliederung im ein Legacy-Sprachdienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gliederung ist es möglich, ein komplexes Programm in einer Übersicht bzw. Gliederung zu reduzieren. In c\# können z. B. alle Methoden in eine einzelne Zeile, und zeigt nur die Signatur der Methode reduziert werden. Darüber hinaus können Strukturen und Klassen reduziert werden, um nur die Namen der Strukturen und Klassen angezeigt. Innerhalb einer einzelnen Methode, komplexe Logik reduziert werden kann, um den Gesamtablauf anzuzeigen, zeigen Sie nur die erste Zeile der Anweisungen wie z. B. `foreach`, `if`, und `while`.  
  
 Ältere Sprache Services werden als Teil eines VSPackage implementiert, aber der neuere Weg zum Implementieren von Language Service ist die Verwendung von MEF\-Erweiterungen. Um weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Gliedern](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor\-API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie die neue Editorfunktionen nutzen.  
  
## Aktivieren der Unterstützung für eine Gliederung  
 Die `AutoOutlining` Registrierungseintrag auf 1 festgelegt ist, um die automatische Gliederung zu aktivieren. Automatische Gliederung richtet eine Analyse der gesamten Datenquelle, wenn eine Datei geladen oder geändert, um ausgeblendete Bereiche zu identifizieren und die Gliederung Symbole anzeigen. Gliederung kann auch manuell vom Benutzer gesteuert werden.  
  
 Der Wert des der `AutoOutlining` Eintrag in der Registrierung erhalten Sie über die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> Eigenschaft auf die <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse. Die `AutoOutlining` Registrierungseintrag kann initialisiert werden, mit einer benannten Parameter, um die <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Attribut \(finden Sie unter [Registriert eine Sprachdienst](../../extensibility/internals/registering-a-legacy-language-service1.md) Details\).  
  
## Die ausgeblendeten Bereich  
 Um Gliederung zu gewährleisten, muss der Sprachdienst ausgeblendete Bereiche unterstützen. Hierbei handelt es sich um eine Passage mit Text, der erweitert oder reduziert werden können. Ausgeblendete Bereiche können durch Standardsprache Symbole, z. B. geschweifte Klammern ein, oder benutzerdefinierte Symbole getrennt werden. C\# hat beispielsweise eine `#region`\/`#endregion` \-Paar, das einen ausgeblendeten Bereich begrenzt.  
  
 Ausgeblendete Bereiche werden von einem ausgeblendeten Bereich\-Manager verfügbar, als gemacht wird verwaltet die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Schnittstelle.  
  
 Gliederung ausgeblendete Bereiche verwendet die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> \-Schnittstelle und enthalten die Spanne der ausgeblendeten Bereich, den aktuellen Sichtbarkeitsstatus und Banner angezeigt werden, wenn die Spanne reduziert wird.  
  
 Der Sprachenparser für den Dienst verwendet die <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> \-Methode zum Hinzufügen einer neuen ausgeblendeten Region mit dem Standardverhalten für ausgeblendete Bereiche während der <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> Methode können Sie das Aussehen und Verhalten der Gliederung anpassen. Sobald die Sitzung ausgeblendeten Bereich ausgeblendete Bereiche zugewiesen werden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ausgeblendete Bereiche für den Sprachdienst verwaltet.  
  
 Wenn Sie müssen bestimmen, wann die ausgeblendeten Bereich Sitzung zerstört wird, ein ausgeblendeten Bereich geändert wird, oder müssen Sie sicherstellen, dass ein bestimmter ausgeblendeter Bereich sichtbar ist; Leiten Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.Source> Klasse, und überschreiben Sie die entsprechenden Methoden <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>, und <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>, bzw..  
  
### Beispiel  
 Hier ist ein vereinfachtes Beispiel ausgeblendete Bereiche für alle Paare von geschweiften Klammern erstellen. Es wird davon ausgegangen, dass die Sprache Klammer bereitstellt, und die geschweiften Klammern abgeglichen wird zumindest die geschweiften Klammern enthalten \({und}\). Dieser Ansatz ist nur zur Veranschaulichung. Eine vollständige Implementierung hätte eine vollständige Behandlung der Fälle im <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>. Dieses Beispiel zeigt auch auf die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> Vorzug `true` vorübergehend. Geben Sie eine Alternative ist die `AutoOutlining` benannten Parameter in der `ProvideLanguageServiceAttribute` Attribut im Language\-Paket.  
  
 C\#\-Regeln für Kommentare, Zeichenfolgen und Literale angenommen.  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
  
    public class MyLanguageService : LanguageService  
    {  
        private LanguagePreferences m_preferences;  
  
        public override LanguagePreferences  GetLanguagePreferences()  
        {  
            if (m_preferences == null)  
            {  
                m_preferences = new LanguagePreferences(this.Site,  
                                                        typeof(MyLanguageService).GUID,  
                                                        Name);  
                m_preferences.Init();  
                // Temporarily enabled auto-outlining  
                m_preferences.AutoOutlining = true;  
            }  
            return m_preferences;  
        }  
  
        public override AuthoringScope  ParseSource(ParseRequest req)  
        {  
            Source source = (Source) this.GetSource(req.FileName);  
            switch (req.Reason)  
            {  
               case ParseReason.HighlightBraces:  
               case ParseReason.MatchBraces:  
               case ParseReason.MemberSelectAndHighlightBraces:  
                  if (source.Braces != null)  
                  {  
                      foreach (TextSpan[] brace in source.Braces)  
                      {  
                         if (brace.Length == 2)  
                         {  
                             if (req.Sink.HiddenRegions == true   
                                   && source.GetText(brace[0]).Equals("{")   
                                   && source.GetText(brace[1]).Equals("}"))  
                             {  
                                //construct a TextSpan of everything between the braces  
                                TextSpan hideSpan = new TextSpan();  
                                hideSpan.iStartIndex = brace[0].iStartIndex;  
                                hideSpan.iStartLine = brace[0].iStartLine;  
                                hideSpan.iEndIndex = brace[1].iEndIndex;  
                                hideSpan.iEndLine = brace[1].iEndLine;  
                                req.Sink.ProcessHiddenRegions = true;  
                                req.Sink.AddHiddenRegion(hideSpan);  
                             }  
                             req.Sink.MatchPair(brace[0], brace[1], 1);  
                         }  
                         else if (brace.Length >= 3)  
                             req.Sink.MatchTriple(brace[0], brace[1], brace[2], 1);  
                  }  
        }  
                   break;  
               default:  
                   break;  
      }  
            // Must always return a valid AuthoringScope object.  
            return new MyAuthoringScope();  
        }  
    }  
}  
```  
  
## Siehe auch  
 [Legacy\-Dienst\-Sprachfunktionen](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registriert eine Sprachdienst](../../extensibility/internals/registering-a-legacy-language-service1.md)