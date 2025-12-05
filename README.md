# Fábrica

# Instructions

- Tiles at the bottom
- Double click to grab the desired tile
- Click to rotate
- Double click to apply
- Right click to discard

# Install & Run

(Linux only)

## Install

- Dependencies

```
sudo apt install libsdl2-dev libsdl2-gfx-dev libsdl2-image-dev libsdl2-mixer-dev libsdl2-ttf-dev
sudo apt install luarocks lua5.4 liblua5.4-dev
sudo luarocks install pico-sdl
sudo luarocks install atmos --lua-version=5.4
sudo luarocks install atmos-lang --lua-version=5.4
```

- Fábrica

```
git clone https://github.com/fsantanna/fabrica
```

## Run

```
cd fabrica/
atmos main.atm
```
