EscapeDeCuba/
├── App.js
├── assets/
│   └── background.png  ← (aquí iría tu fondo estilo Malecón)
├── screens/
│   └── HomeScreen.js
│   └── GameScreen.js
│   └── OptionsScreen.js
│   └── CreditsScreen.js
import React from 'react';
import { NavigationContainer } from '@react-navigation/native';
import { createNativeStackNavigator } from '@react-navigation/native-stack';
import HomeScreen from './screens/HomeScreen';
import GameScreen from './screens/GameScreen';
import OptionsScreen from './screens/OptionsScreen';
import CreditsScreen from './screens/CreditsScreen';

const Stack = createNativeStackNavigator();

export default function App() {
  return (
    <NavigationContainer>
      <Stack.Navigator initialRouteName="Inicio" screenOptions={{ headerShown: false }}>
        <Stack.Screen name="Inicio" component={HomeScreen} />
        <Stack.Screen name="Juego" component={GameScreen} />
        <Stack.Screen name="Opciones" component={OptionsScreen} />
        <Stack.Screen name="Créditos" component={CreditsScreen} />
      </Stack.Navigator>
    </NavigationContainer>
  );
}
import React from 'react';
import { View, Text, ImageBackground, TouchableOpacity, StyleSheet } from 'react-native';

export default function HomeScreen({ navigation }) {
  return (
    <ImageBackground source={require('../assets/background.png')} style={styles.background}>
      <Text style={styles.title}>ESCAPE DE CUBA</Text>

      <TouchableOpacity style={styles.button} onPress={() => navigation.navigate('Juego')}>
        <Text style={styles.buttonText}>JUGAR</Text>
      </TouchableOpacity>

      <TouchableOpacity style={styles.button} onPress={() => navigation.navigate('Opciones')}>
        <Text style={styles.buttonText}>OPCIONES</Text>
      </TouchableOpacity>

      <TouchableOpacity style={styles.button} onPress={() => navigation.navigate('Créditos')}>
        <Text style={styles.buttonText}>CRÉDITOS</Text>
      </TouchableOpacity>
    </ImageBackground>
  );
}

const styles = StyleSheet.create({
  background: {
    flex: 1,
    resizeMode: 'cover',
    justifyContent: 'center',
    alignItems: 'center',
  },
  title: {
    fontSize: 36,
    color: '#f4e6c0',
    fontWeight: 'bold',
    marginBottom: 50,
    fontFamily: 'monospace',
  },
  button: {
    backgroundColor: '#f4e6c0',
    paddingVertical: 15,
    paddingHorizontal: 60,
    borderRadius: 10,
    marginVertical: 10,
  },
  buttonText: {
    fontSize: 20,
    color: '#333',
    fontWeight: 'bold',
  },
});
