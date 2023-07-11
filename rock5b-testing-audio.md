# Rock5B testing audio card(s)

Currently we do only support analog audio through the 3.5mm jack connector, which
is controlled by the ES8316 Audio Codec.

The HDMI audio support will be added later.

## Analog audio setup & testing

Before proceeding with the steps below, please verify the sound card is
correctly registered. Also make sure all the commands are executed as root!

```console
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: rk3588es8316 [rk3588-es8316], device 0: fe470000.i2s-ES8316 HiFi ES8316 HiFi-0 [fe470000.i2s-ES8316 HiFi ES8316 HiFi-0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

### Enable analog audio output & input

```console
$ alsaucm -c rk3588-es8316 reset reload set _verb HiFi list _devices set _enadev Headphones set _enadev Headset
```

### Test playback

```console
$ speaker-test -D hw:rk3588es8316,0 -F S16_LE -c 2 -t wav
```

### Record a short audio

```console
$ arecord -D hw:rk3588es8316,0 -f S16_LE -c 2 -r 48000 -d 5 -V stereo /tmp/test.wav
```

### Play recorded audio file

```console
$ aplay -D hw:rk3588es8316,0 -V stereo /tmp/test.wav
```
