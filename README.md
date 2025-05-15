# saleswriter-ai
 An AI tool that writes high-converting sales copy.
 import streamlit as st
import openai

st.title("AI Sales Copy Generator")

# API-Key sicher aus secrets laden
openai.api_key = st.secrets["OPENAI_API_KEY"]

# Hier steht der Text, den der Nutzer eingibt (Produktbeschreibung)
prompt = st.text_area("Produktbeschreibung eingeben:")

if st.button("Verkaufs-Text generieren"):
    if prompt:
        response = openai.Completion.create(
            engine="text-davinci-003",
            prompt=f"Schreibe einen überzeugenden Verkaufstext für folgendes Produkt: {prompt}",
            max_tokens=150,
            temperature=0.7
        )
        st.write(response.choices[0].text.strip())
    else:
        st.error("Bitte zuerst eine Produktbeschreibung eingeben.")
