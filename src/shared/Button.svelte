<button>
    <slot></slot>
</button>

<style>
	button {
		height: 4rem;
		width: 8rem;
		background-color: #2081C3;
        border-color: #2081C3;
        border-radius: 10px;
        cursor: pointer;
		color: #ffffff;
		font-size: 1.25rem;
		background-image: linear-gradient(45deg, #63D2FF 50%, transparent 50%);
		background-position: 100%;
		background-size: 400%;
		transition: background 300ms ease-in-out;
	}
	button:hover {
		background-position: 0;
		color: #fff;
	}
</style>