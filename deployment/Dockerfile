FROM python:3.9

# Set up user and environment
RUN useradd -m -u 1000 user
USER user
ENV HOME=/home/user \
    PATH=/home/user/.local/bin:$PATH

WORKDIR $HOME/app

# Install requirements
COPY --chown=user requirements.txt $HOME/app/requirements.txt
RUN pip install --no-cache-dir --user -r requirements.txt

# Copy app files
COPY --chown=user . $HOME/app

# Standard port for HF Spaces
EXPOSE 7860

# Start streamlit directly
CMD streamlit run app.py --server.port 7860 --server.address 0.0.0.0
