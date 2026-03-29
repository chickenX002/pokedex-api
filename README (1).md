# 🎮 Pokédex API - Free GitHub-Hosted Database

A **free, open-source Pokédex API** with complete data for all **1,350 Pokémon entries** including all regional forms, mega evolutions, Gigantamax forms, and special variants!

## 🌟 Features

- ✅ **1,350 Total Pokémon** (1,025 base + 325 variants)
- ✅ **All Regional Forms** (Alolan, Galarian, Hisuian, Paldean)
- ✅ **All Mega Evolutions**
- ✅ **All Gigantamax Forms**
- ✅ **All Special Variants** (Totem, Primal, forms, etc.)
- ✅ **100% FREE** - No API keys, no rate limits, no costs
- ✅ **Hosted on GitHub** - Fast, reliable, worldwide CDN
- ✅ **Offline-capable** - Download the whole database
- ✅ **Open Source** - Contribute, fork, improve!

## 📊 Data Structure

Each Pokémon entry contains:
```json
{
  "id": 26,
  "name": "raichu-alola",
  "types": ["electric", "psychic"],
  "entry": "It uses psychic power to control electricity..."
}
```

### Smart ID System
All variants share the same ID as their base form:
- **Raichu** (base) → ID 26
- **Alolan Raichu** → ID 26
- **Mega Charizard X** → ID 6
- **Gigantamax Pikachu** → ID 25

This makes it easy to fetch sprites from PokeAPI's GitHub:
```
https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/{id}.png
```

## 🚀 Usage

### Get the Full Database
```
https://raw.githubusercontent.com/yourusername/pokedex-api/main/pokemon_data_remapped.json
```

### JavaScript Example
```javascript
// Fetch all Pokémon data
const response = await fetch('https://raw.githubusercontent.com/yourusername/pokedex-api/main/pokemon_data_remapped.json');
const pokemon = await response.json();

// Find Pikachu
const pikachu = pokemon.find(p => p.name === 'pikachu');
console.log(pikachu);

// Get all Pikachu variants (all have ID 25)
const pikachu_variants = pokemon.filter(p => p.id === 25);
console.log(`Found ${pikachu_variants.length} Pikachu variants`);
```

### Python Example
```python
import requests

# Load full database
url = 'https://raw.githubusercontent.com/yourusername/pokedex-api/main/pokemon_data_remapped.json'
response = requests.get(url)
pokemon = response.json()

# Find Alolan Raichu
alolan_raichu = next(p for p in pokemon if p['name'] == 'raichu-alola')
print(f"ID: {alolan_raichu['id']}")
print(f"Types: {alolan_raichu['types']}")
print(f"Entry: {alolan_raichu['entry']}")

# Get sprite URL
sprite_url = f"https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/{alolan_raichu['id']}.png"
print(f"Sprite: {sprite_url}")
```

## 📈 Statistics

- **Total Entries**: 1,350
- **Base Pokémon**: 1,025 (Gen 1-9)
- **Alolan Forms**: 18
- **Galarian Forms**: 19
- **Hisuian Forms**: 17
- **Mega Evolutions**: 48
- **Gigantamax Forms**: 32
- **Other Variants**: 191+

### Pokémon with Most Variants
1. **Pikachu** (ID 25) - 17 forms
2. **Minior** (ID 774) - 14 forms
3. **Rotom** (ID 479) - 6 forms
4. **Zygarde** (ID 718) - 6 forms
5. **Charizard** (ID 6) - 4 forms

## 🎨 Getting Sprites

All sprites are hosted on PokeAPI's GitHub:

```
Base URL: https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/

Examples:
- Pikachu: .../25.png
- Alolan Raichu: .../26.png (same as regular Raichu)
- Mega Charizard X: .../6.png (same as regular Charizard)
```

**Note**: The sprite URL uses the **base ID**, so all variants of a Pokémon share the same sprite URL.

## 🔍 Search Examples

### Find by Name (Exact)
```javascript
const charizard = pokemon.find(p => p.name === 'charizard');
```

### Find by Name (Partial)
```javascript
const char_pokemon = pokemon.filter(p => p.name.includes('char'));
// Returns: charmander, charmeleon, charizard, charizard-mega-x, etc.
```

### Find by ID (Get all variants)
```javascript
const raichu_variants = pokemon.filter(p => p.id === 26);
// Returns: raichu, raichu-alola, raichu-mega-x, raichu-mega-y
```

### Find by Type
```javascript
const fire_pokemon = pokemon.filter(p => p.types.includes('fire'));
```

### Get All Mega Evolutions
```javascript
const megas = pokemon.filter(p => p.name.includes('-mega'));
```

### Get All Alolan Forms
```javascript
const alolan = pokemon.filter(p => p.name.includes('-alola'));
```

## 📦 Installation for Offline Use

```bash
# Clone the repository
git clone https://github.com/yourusername/pokedex-api.git

# Or download just the database
wget https://raw.githubusercontent.com/yourusername/pokedex-api/main/pokemon_data_remapped.json
```

## 🤝 Contributing

Found an error? Want to add more data? Contributions are welcome!

1. Fork the repository
2. Make your changes
3. Submit a pull request

## 📜 License

This project is open source under the MIT License.

**Note**: Pokémon names, sprites, and related content are © Nintendo, Game Freak, Creatures Inc. This is a fan project for educational and non-commercial use only.

## 🙏 Credits

- **Data Source**: Original data compiled from various sources
- **Sprites**: [PokeAPI Sprites GitHub](https://github.com/PokeAPI/sprites)
- **Inspiration**: PokeAPI.co

## 💡 Use Cases

This API is perfect for:
- Pokémon fan websites
- Mobile apps
- Discord bots
- Educational projects
- Data analysis
- Machine learning projects
- Game development
- Pokédex applications

## 🌐 No Rate Limits!

Unlike many APIs, GitHub raw content has NO rate limits for reasonable use. Your users can fetch data as many times as needed without worrying about API quotas or costs!

## 📱 Example Projects Using This API

*Coming soon - submit your projects via PR!*

---

**Made with ❤️ by the Pokémon community**

⭐ Star this repo if you find it useful!
