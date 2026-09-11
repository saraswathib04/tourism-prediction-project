FROM python:3.9

# Set up a non-root user for Hugging Face Spaces
RUN useradd -m -u 1000 user
USER user
ENV HOME=/home/user \
    PATH=/home/user/.local/bin:$PATH

WORKDIR $HOME/app

# Copy requirements first to leverage Docker cache
COPY --chown=user requirements.txt $HOME/app/requirements.txt
RUN pip install --no-cache-dir --user --upgrade -r requirements.txt

# Copy the rest of the application files
COPY --chown=user . $HOME/app

# Expose the default Hugging Face Space port
EXPOSE 7860

# Define the entrypoint to launch the Streamlit server
ENTRYPOINT ["streamlit", "run", "app.py", "--server.port", "7860", "--server.address", "0.0.0.0"]
