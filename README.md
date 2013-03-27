Shine-MP3-Encoder-on-AS3-Alchemy
================================

Flash/Alchemy port of the lightweight Shine MP3 Encoder

##Readme
from: https://code.google.com/p/flash-kikko/

### Description
Shine (formely 8hz-MP3) is a simple lightweight C-based MP3 encoder made by LAME developer Gabriel Bouvigne.

#### Description of Shine on his website:

> The goal of this encoder was not quality, but simplicity. I tryed to simplify the encoding process as much as possible. So Shine is then a good starting point when a programmer needs a very simple MP3 encoder

#### This Alchemy port features:
* MP3 encoding of mono and stereo WAVs (no time limit)
* non-blocking encoding for progress status in flash
* errors automatically sent to flash for easy log/debug

Also, thanks to Bernard Hilger Visscher for his very helpful blog post http://blog.debit.nl/?p=67

### Usage
```actionscript
import fr.kikko.lab.ShineMP3Encoder;

private function encodeToMP3(wavData:ByteArray):void {
                        
        mp3Encoder = new ShineMP3Encoder(wavData);
        mp3Encoder.addEventListener(Event.COMPLETE, mp3EncodeComplete);
        mp3Encoder.addEventListener(ProgressEvent.PROGRESS, mp3EncodeProgress);
        mp3Encoder.addEventListener(ErrorEvent.ERROR, mp3EncodeError);
        mp3Encoder.start();
}

private function mp3EncodeProgress(event : ProgressEvent) : void {
                        
        trace(event.bytesLoaded, event.bytesTotal);
}

private function mp3EncodeError(event : ErrorEvent) : void {
                        
        trace("Error : ", event.text);
}

private function mp3EncodeComplete(event : Event) : void {
                        
        trace("Done !", mp3Encoder.mp3Data.length);
}
```
