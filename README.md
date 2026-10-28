# QuietRingtones catalog

Short classical clips for the [QuietRingtones](https://github.com/Quiet115/QuietRingtones) Android app. The app lists them in an "Online catalog" section: tapping play downloads the clip to a cache so you can hear it, and tapping *Use* saves it as your ringtone, notification or alarm sound.

## What is here

- `catalog.json`: the index the app reads.
- `clips/`: the audio, Ogg Vorbis, 30 seconds for ringtones and alarms and 6 seconds for notifications. About 4 MB in total.

## How the clips are made

Each clip comes from a recording that is in the public domain or released under CC0 on Wikimedia Commons. The start is trimmed of silence, the level is normalized, and the end fades out:

```
ffmpeg -i source.ogg -af "silenceremove=start_periods=1:start_threshold=-50dB:start_silence=0.1,afade=t=in:d=0.05,afade=t=out:st=27.5:d=2.5,loudnorm=I=-18:TP=-1.5:LRA=11" -t 30 -ar 44100 -c:a libvorbis -q:a 4 clip.ogg
```

## Sounds

| Title | Artist | For | Length | License | Original |
| --- | --- | --- | --- | --- | --- |
| Air on the G String | Johann Sebastian Bach | ringtone, alarm | 30 s | Public domain | [source](https://commons.wikimedia.org/wiki/File:Air_(Bach).ogg) |
| Toccata and Fugue in D minor | Johann Sebastian Bach | ringtone, alarm | 30 s | Public domain | [source](https://commons.wikimedia.org/wiki/File:Toccata_et_Fugue_BWV565.ogg) |
| Symphony No. 5, I. Allegro con brio | Ludwig van Beethoven | ringtone, alarm | 30 s | Public domain | [source](https://commons.wikimedia.org/wiki/File:Ludwig_van_Beethoven_-_symphony_no._5_in_c_minor%2C_op._67_-_i._allegro_con_brio.ogg) |
| Symphony No. 5, I. Allegro con brio (short) | Ludwig van Beethoven | notification | 6 s | Public domain | [source](https://commons.wikimedia.org/wiki/File:Ludwig_van_Beethoven_-_symphony_no._5_in_c_minor%2C_op._67_-_i._allegro_con_brio.ogg) |
| Ride of the Valkyries | Richard Wagner | ringtone, alarm | 30 s | Public domain | [source](https://commons.wikimedia.org/wiki/File:Richard_Wagner_-_Ride_of_the_Valkyries.ogg) |
| Gymnopédie No. 1 | Erik Satie | ringtone, alarm | 30 s | CC0 | [source](https://commons.wikimedia.org/wiki/File:Gymnopedie_No._1..ogg) |
| Gymnopédie No. 1 (short) | Erik Satie | notification | 6 s | CC0 | [source](https://commons.wikimedia.org/wiki/File:Gymnopedie_No._1..ogg) |
| The Blue Danube | Johann Strauss II | ringtone, alarm | 30 s | CC0 | [source](https://commons.wikimedia.org/wiki/File:Strauss%2C_An_der_sch%C3%B6nen_blauen_Donau.ogg) |
| Carmen, Prelude to Act 1 | Georges Bizet | ringtone, alarm | 30 s | CC0 | [source](https://commons.wikimedia.org/wiki/File:Carmen_-_Prelude_to_Act_1.ogg) |
| Carmen, Prelude to Act 1 (short) | Georges Bizet | notification | 6 s | CC0 | [source](https://commons.wikimedia.org/wiki/File:Carmen_-_Prelude_to_Act_1.ogg) |
| Nocturne in E-flat major, Op. 9 No. 2 | Frédéric Chopin | ringtone, alarm | 30 s | CC0 | [source](https://commons.wikimedia.org/wiki/File:Chopin_Nocturne_No._2_in_E_Flat_Major%2C_Op._9.ogg) |
| Nocturne in E-flat major, Op. 9 No. 2 (short) | Frédéric Chopin | notification | 6 s | CC0 | [source](https://commons.wikimedia.org/wiki/File:Chopin_Nocturne_No._2_in_E_Flat_Major%2C_Op._9.ogg) |
| Clair de lune | Claude Debussy | ringtone, alarm | 30 s | Public domain | [source](https://commons.wikimedia.org/wiki/File:Clair_de_lune_(Claude_Debussy)_Suite_bergamasque.ogg) |
| Swan Lake, Waltz | Pyotr Ilyich Tchaikovsky | ringtone, alarm | 30 s | Public domain | [source](https://commons.wikimedia.org/wiki/File:Tchaikovsky_Swan_Lake_Op.20_No.2.Waltz.ogg) |
| Eine kleine Nachtmusik, I. Allegro | Wolfgang Amadeus Mozart | ringtone, alarm | 30 s | Public domain | [source](https://commons.wikimedia.org/wiki/File:Mozart_K525_Serenade_in_G_Major_1_-_Allegro.ogg) |
| Eine kleine Nachtmusik, I. Allegro (short) | Wolfgang Amadeus Mozart | notification | 6 s | Public domain | [source](https://commons.wikimedia.org/wiki/File:Mozart_K525_Serenade_in_G_Major_1_-_Allegro.ogg) |

No attribution is required for public-domain or CC0 recordings; the sources are listed anyway.

## Format of catalog.json

```json
{
  "version": 1,
  "sounds": [
    {
      "id": "bach-air",
      "title": "Air on the G String",
      "artist": "Johann Sebastian Bach",
      "kinds": ["ringtone", "alarm"],
      "file": "clips/bach-air.ogg",
      "seconds": 30.0,
      "bytes": 388941,
      "sha256": "…",
      "license": "Public domain",
      "source": "https://commons.wikimedia.org/wiki/File:…"
    }
  ]
}
```

`kinds` is any of `ringtone`, `notification` and `alarm`. The app checks each downloaded clip against `sha256`.

## Adding a sound

Only recordings that are in the public domain or CC0 (check the license on the Commons file page), or that you made yourself. Add the clip under `clips/`, add its entry to `catalog.json` with the real size and SHA-256, and list its source above.

## License

The index (`catalog.json`) and this text are released under [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/). The clips come from the public-domain or CC0 recordings linked in the table.